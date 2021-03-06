---
title: OracleTypes
ms.date: 03/30/2017
ms.assetid: 18143304-d5c7-4c95-9995-678088d0c142
ms.openlocfilehash: 95a1173dfbcc4cf49ded8c7b8a42d9764fee9aff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149400"
---
# <a name="oracletypes"></a>OracleTypes
Der .NET Framework-Datenanbieter für Oracle enthält mehrere Strukturen, die für das Arbeiten mit Oracle-Datentypen verwendet werden können. Dazu gehören <xref:System.Data.OracleClient.OracleNumber> und <xref:System.Data.OracleClient.OracleString>.  
  
> [!NOTE]
> Eine vollständige Liste dieser Strukturen finden Sie unter <xref:System.Data.OracleClient>.  
  
 In den unten stehenden C#-Beispielen werden folgende Aktionen ausgeführt:  
  
- Erstellen einer Oracle-Tabelle, die anschließend mit Daten gefüllt wird.  
  
- Zugriff auf die Daten mithilfe eines <xref:System.Data.OracleClient.OracleDataReader>. Das Darstellen der Daten erfolgt mithilfe mehrerer <xref:System.Data.OracleClient.OracleType>-Strukturen.  
  
## <a name="creating-an-oracle-table"></a>Erstellen einer Oracle-Tabelle  
 In diesem Beispiel wird eine Oracle-Tabelle erstellt, die anschließend mit Daten gefüllt wird. Sie müssen dieses Beispiel ausführen, bevor das nächste Beispiel ausgeführt wird.  
  
```csharp  
public void Setup(string connectionString)  
   {  
   OracleConnection conn = new OracleConnection(connectionString);  
   try  
      {  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
      cmd.CommandText ="CREATE TABLE OracleTypesTable " +  
        "(MyVarchar2 varchar2(3000),MyNumber number(28,4) " +  
        "PRIMARY KEY ,MyDate date, MyRaw raw(255))";  
      cmd.ExecuteNonQuery();  
      cmd.CommandText ="INSERT INTO OracleTypesTable VALUES " +  
        "( 'test', 2, to_date('2000-01-11 12:54:01','yyyy-mm-dd " +  
        "hh24:mi:ss'), '0001020304' )";  
      cmd.ExecuteNonQuery();  
      }  
   catch(Exception)  
   {  
   }  
   finally  
   {  
      conn.Close();  
   }  
}  
```  
  
## <a name="retrieving-data-from-the-oracle-table"></a>Abrufen von Daten aus der Oracle-Tabelle  
 In diesem Beispiel wird ein **OracleDataReader** für den Zugriff auf die Daten verwendet und mehrere **OracleType-Strukturen** zum Anzeigen der Daten verwendet.  
  
```csharp  
public void ReadOracleTypesExample(string connectionString)  
   {  
   OracleConnection myConnection =
      new OracleConnection(connectionString);  
   myConnection.Open();  
   OracleCommand myCommand = myConnection.CreateCommand();  
  
   try  
      {  
      myCommand.CommandText = "SELECT * from OracleTypesTable";  
      OracleDataReader oracledatareader1 = myCommand.ExecuteReader();  
      oracledatareader1.Read();  
  
      //Using the oracle specific getters for each type is faster than  
      //using GetOracleValue.  
  
      //First column, MyVarchar2, is a VARCHAR2 data type in Oracle  
      //Server and maps to OracleString.  
      OracleString oraclestring1 =
        oracledatareader1.GetOracleString(0);  
      Console.WriteLine("OracleString " + oraclestring1.ToString());  
  
      //Second column, MyNumber, is a NUMBER data type in Oracle Server  
      //and maps to OracleNumber.  
      OracleNumber oraclenumber1 =
        oracledatareader1.GetOracleNumber(1);  
      Console.WriteLine("OracleNumber " + oraclenumber1.ToString());  
  
      //Third column, MyDate, is a DATA data type in Oracle Server  
      //and maps to OracleDateTime.  
      OracleDateTime oracledatetime1 =
        oracledatareader1.GetOracleDateTime(2);  
      Console.WriteLine("OracleDateTime " + oracledatetime1.ToString());  
  
      //Fourth column, MyRaw, is a RAW data type in Oracle Server and  
      //maps to OracleBinary.  
      OracleBinary oraclebinary1 =
        oracledatareader1.GetOracleBinary(3);  
      //Calling value on a null OracleBinary throws  
      //OracleNullValueException; therefore, check for a null value.  
      if (oraclebinary1.IsNull==false)  
      {  
         foreach(byte b in oraclebinary1.Value)  
         {  
            Console.WriteLine("byte " + b.ToString());  
         }  
      }  
      oracledatareader1.Close();  
   }  
   catch(Exception e)  
   {  
       Console.WriteLine(e.ToString());  
   }  
   finally  
   {  
       myConnection.Close();  
   }  
}  
```  
  
## <a name="see-also"></a>Weitere Informationen

- [Oracle und ADO.NET](oracle-and-adonet.md)
- [Übersicht über ADO.NET](ado-net-overview.md)
