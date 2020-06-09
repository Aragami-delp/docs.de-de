---
title: 'Vorgehensweise: Authentifizierung mit Benutzernamen und Kennwort'
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF], user name and password
ms.assetid: a5415be2-0ef3-464c-9f76-c255cb8165a4
ms.openlocfilehash: e8dc9177afc590a6467855decfa8450b37c6fc77
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601282"
---
# <a name="how-to-authenticate-with-a-user-name-and-password"></a><span data-ttu-id="f08d4-102">Vorgehensweise: Authentifizierung mit Benutzernamen und Kennwort</span><span class="sxs-lookup"><span data-stu-id="f08d4-102">How to: Authenticate with a User Name and Password</span></span>

<span data-ttu-id="f08d4-103">In diesem Thema wird veranschaulicht, wie ein Windows Communication Foundation (WCF)-Dienst zum Authentifizieren eines Clients mit einem Benutzernamen und einem Kennwort für Windows-Domäne aktiviert wird.</span><span class="sxs-lookup"><span data-stu-id="f08d4-103">This topic demonstrates how to enable a Windows Communication Foundation (WCF) service to authenticate a client with a Windows domain username and password.</span></span> <span data-ttu-id="f08d4-104">Es wird davon ausgegangen, dass Sie über einen funktionsfähigen selbst gehosteten WCF-Dienst verfügen.</span><span class="sxs-lookup"><span data-stu-id="f08d4-104">It assumes you have a working, self-hosted WCF service.</span></span> <span data-ttu-id="f08d4-105">Ein Beispiel für das Erstellen eines selbst gehosteten WCF-Dienstanbieter finden Sie unter " [Getting Started Tutorial](../getting-started-tutorial.md)".</span><span class="sxs-lookup"><span data-stu-id="f08d4-105">For an example of creating a basic self-hosted WCF service see, [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="f08d4-106">In diesem Thema wird davon ausgegangen, dass der Dienst im Code konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="f08d4-106">This topic assumes the service is configured in code.</span></span> <span data-ttu-id="f08d4-107">Ein Beispiel für die Konfiguration eines ähnlichen Diensts mithilfe einer Konfigurationsdatei finden Sie unter [Message Security User Name](../samples/message-security-user-name.md).</span><span class="sxs-lookup"><span data-stu-id="f08d4-107">If you would like to see an example of configuring a similar service using a configuration file, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>

<span data-ttu-id="f08d4-108">Um einen Dienst zu konfigurieren, der seine Clients mit dem Benutzernamen und Kennwort einer Windows-Domäne authentifiziert, verwenden Sie die <xref:System.ServiceModel.WSHttpBinding> und legen die `Security.Mode`-Eigenschaft auf `Message` fest.</span><span class="sxs-lookup"><span data-stu-id="f08d4-108">To configure a service to authenticate its clients using Windows Domain username and passwords use the <xref:System.ServiceModel.WSHttpBinding> and set its `Security.Mode` property to `Message`.</span></span> <span data-ttu-id="f08d4-109">Darüber hinaus müssen Sie ein X.509-Zertifikat angeben, das zum Verschlüsseln des Benutzernamens und Kennworts verwendet wird, während diese vom Client an den Dienst gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="f08d4-109">In addition you must specify an X509 certificate that will be used to encrypt the username and password as they are sent from the client to the service.</span></span>

<span data-ttu-id="f08d4-110">Auf dem Client muss der Benutzer zur Eingabe des Benutzernamens und Kennworts und zur Eingabe der Anmeldeinformationen für den WCF-Clientproxy aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="f08d4-110">On the client, you must prompt the user for the username and password and specify the user’s credentials on the WCF client proxy.</span></span>

## <a name="to-configure-a-wcf-service-to-authenticate-using-windows-domain-username-and-password"></a><span data-ttu-id="f08d4-111">So konfigurieren Sie einen WCF-Dienst für die Authentifizierung mit Windows-Domänen Benutzername und Kennwort</span><span class="sxs-lookup"><span data-stu-id="f08d4-111">To configure a WCF service to authenticate using Windows domain username and password</span></span>

1. <span data-ttu-id="f08d4-112">Erstellen Sie eine Instanz von <xref:System.ServiceModel.WSHttpBinding>, legen Sie den Sicherheitsmodus der Bindung auf <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType> fest, legen Sie den `ClientCredentialType` der Bindung auf <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType> fest, und fügen Sie dem Diensthost mithilfe der konfigurierten Bindung einen Dienstendpunkt hinzu, wie im folgenden Code dargestellt:</span><span class="sxs-lookup"><span data-stu-id="f08d4-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding>, set the security mode of the binding to <xref:System.ServiceModel.WSHttpSecurity.Message?displayProperty=nameWithType>, set the `ClientCredentialType` of the binding to <xref:System.ServiceModel.MessageCredentialType.UserName?displayProperty=nameWithType>, and add a service endpoint using the configured binding to the service host as shown in the following code:</span></span>

    ```csharp
    // ...
    var userNameBinding = new WSHttpBinding();
    userNameBinding.Security.Mode = SecurityMode.Message;
    userNameBinding.Security.Message.ClientCredentialType = MessageCredentialType.UserName;
    svcHost.AddServiceEndpoint(typeof(IService1), userNameBinding, "");
    // ...
    ```

2. <span data-ttu-id="f08d4-113">Geben Sie das Serverzertifikat an, das zum Verschlüsseln des über die Verbindung gesendeten Benutzernamens und Kennworts verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="f08d4-113">Specify the server certificate used to encrypt the username and password information sent over the wire.</span></span> <span data-ttu-id="f08d4-114">Dieser Code sollte direkt auf den vorangehenden Code folgen.</span><span class="sxs-lookup"><span data-stu-id="f08d4-114">This code should immediately follow the code above.</span></span> <span data-ttu-id="f08d4-115">Im folgenden Beispiel wird das Zertifikat verwendet, das von der Datei "Setup. bat" aus dem Beispiel für den [Nachrichten Sicherheits Benutzernamen](../samples/message-security-user-name.md) erstellt wurde:</span><span class="sxs-lookup"><span data-stu-id="f08d4-115">The following example uses the certificate that is created by the setup.bat file from the [Message Security User Name](../samples/message-security-user-name.md) sample:</span></span>

    ```csharp
    // ...
    svcHost.Credentials.ServiceCertificate.SetCertificate(StoreLocation.LocalMachine, StoreName.My, X509FindType.FindBySubjectName, "localhost");
    // ...
    ```

    <span data-ttu-id="f08d4-116">Sie können ein eigenes Zertifikat verwenden, indem Sie im Code auf das eigene Zertifikat verweisen.</span><span class="sxs-lookup"><span data-stu-id="f08d4-116">You can use your own certificate, just modify the code to refer to your certificate.</span></span> <span data-ttu-id="f08d4-117">Weitere Informationen zum Erstellen und Verwenden von Zertifikaten finden Sie [unter Arbeiten mit Zertifikaten](working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f08d4-117">For more information about creating and using certificates see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="f08d4-118">Stellen Sie sicher, dass sich das Zertifikat im Speicher für vertrauenswürdige Personen für den lokalen Computer befindet.</span><span class="sxs-lookup"><span data-stu-id="f08d4-118">Make sure the certificate is in the Trusted People certificate store for the Local Machine.</span></span> <span data-ttu-id="f08d4-119">Hierzu können Sie MMC. exe ausführen und das Menü Element **Datei**, **Snap-in hinzufügen/entfernen** auswählen.</span><span class="sxs-lookup"><span data-stu-id="f08d4-119">You can do this by running mmc.exe and selecting the **File**, **Add/Remove Snap-in...** menu item.</span></span> <span data-ttu-id="f08d4-120">Wählen Sie im Dialogfeld **Snap-Ins hinzufügen bzw. entfernen** das **Zertifikat-Snap-in** aus, und klicken Sie auf **Hinzufügen**.</span><span class="sxs-lookup"><span data-stu-id="f08d4-120">In the **Add or Remove Snap-ins** dialog, select the **Certificates snap-in** and click **Add**.</span></span> <span data-ttu-id="f08d4-121">Wählen Sie im Dialogfeld Zertifikate-Snap-in die Option **Computer Konto**aus.</span><span class="sxs-lookup"><span data-stu-id="f08d4-121">In the Certificates Snap-in dialog select **Computer account**.</span></span> <span data-ttu-id="f08d4-122">Standardmäßig befindet sich das Zertifikat, das im Beispiel für Nachrichtensicherheit – Benutzername generiert wurde, im Ordner Persönlich – Zertifikate.</span><span class="sxs-lookup"><span data-stu-id="f08d4-122">By default the certificate generated from the Message Security User name sample will be located in the Personal/Certificates folder.</span></span>  <span data-ttu-id="f08d4-123">Sie wird in der Spalte ausgestellt für im MMC-Fenster als "localhost" aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="f08d4-123">It will be listed as "localhost" under the Issued to column in the MMC window.</span></span> <span data-ttu-id="f08d4-124">Ziehen Sie das Zertifikat per Drag & Drop in den Ordner **Vertrauenswürdige Personen** .</span><span class="sxs-lookup"><span data-stu-id="f08d4-124">Drag and drop the certificate into the **Trusted People** folder.</span></span> <span data-ttu-id="f08d4-125">Dadurch kann WCF das Zertifikat beim Ausführen einer Authentifizierung als vertrauenswürdiges Zertifikat behandeln.</span><span class="sxs-lookup"><span data-stu-id="f08d4-125">This will allow WCF to treat the certificate as a trusted certificate when performing authentication.</span></span>

## <a name="to-call-the-service-passing-username-and-password"></a><span data-ttu-id="f08d4-126">So rufen Sie den Dienst auf, der den Benutzernamen und das Kennwort übergibt</span><span class="sxs-lookup"><span data-stu-id="f08d4-126">To call the service passing username and password</span></span>

1. <span data-ttu-id="f08d4-127">Die Clientanwendung muss den Benutzer zur Eingabe von Benutzername und Kennwort auffordern.</span><span class="sxs-lookup"><span data-stu-id="f08d4-127">The client application must prompt the user for their username and password.</span></span> <span data-ttu-id="f08d4-128">Der folgende Code fragt den Benutzer nach Benutzername und Kennwort:</span><span class="sxs-lookup"><span data-stu-id="f08d4-128">The following code asks the user for username and password:</span></span>

    > [!WARNING]
    > <span data-ttu-id="f08d4-129">Dieser Code sollte nicht in Produktionssystemen verwendet werden, da das Kennwort bei der Eingabe sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="f08d4-129">This code should not be used in production as the password is displayed while being entered.</span></span>

    ```csharp
    public static void GetPassword(out string username, out string password)
    {
        Console.WriteLine("Provide a valid machine or domain account. [domain\\user]");
        Console.WriteLine("   Enter username:");
        username = Console.ReadLine();
        Console.WriteLine("   Enter password:");
        password = Console.ReadLine();
    }
    ```

2. <span data-ttu-id="f08d4-130">Erstellen Sie eine Instanz des Client Proxys, indem Sie die Anmelde Informationen des Clients angeben, wie im folgenden Code gezeigt:</span><span class="sxs-lookup"><span data-stu-id="f08d4-130">Create an instance of the client proxy specifying the client's credentials as shown in the following code:</span></span>

    ```csharp
    string username;
    string password;

    // Instantiate the proxy.
    var proxy = new Service1Client();

    // Prompt the user for username & password.
    GetPassword(out username, out password);

    // Set the user's credentials on the proxy.
    proxy.ClientCredentials.UserName.UserName = username;
    proxy.ClientCredentials.UserName.Password = password;

    // Treat the test certificate as trusted.
    proxy.ClientCredentials.ServiceCertificate.Authentication.CertificateValidationMode = System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust;
    // Call the service operation using the proxy
    ```

## <a name="see-also"></a><span data-ttu-id="f08d4-131">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f08d4-131">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.SecurityMode>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.UserName%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential.Password%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- <xref:System.ServiceModel.WSHttpSecurity.Mode%2A>
- <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>
- [<span data-ttu-id="f08d4-132">Transportsicherheit mit Standardauthentifizierung</span><span class="sxs-lookup"><span data-stu-id="f08d4-132">Transport Security with Basic Authentication</span></span>](transport-security-with-basic-authentication.md)
- [<span data-ttu-id="f08d4-133">Sicherheit bei verteilten Anwendungen</span><span class="sxs-lookup"><span data-stu-id="f08d4-133">Distributed Application Security</span></span>](distributed-application-security.md)
- [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)
