---
title: Aktualisieren von Datenquellen mit "DataAdapters"
description: Erfahren Sie, wie die Update-Methode von DataAdapter Änderungen von einem DataSet zurück in die Datenquelle in ADO.NET-Anwendungen auflöst.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1bd9a8c-0e29-40e3-bda8-d89176b72fb1
ms.openlocfilehash: e2348a3a89aa1c28856bfc21aaa25f2c8327aac7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286183"
---
# <a name="updating-data-sources-with-dataadapters"></a><span data-ttu-id="2e89e-103">Aktualisieren von Datenquellen mit "DataAdapters"</span><span class="sxs-lookup"><span data-stu-id="2e89e-103">Updating Data Sources with DataAdapters</span></span>

<span data-ttu-id="2e89e-104">Zum Aktualisieren von Datenquellen mit den Änderungen, die an einem `Update` vorgenommen wurden, wird die <xref:System.Data.Common.DataAdapter>-Methode des <xref:System.Data.DataSet> aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-104">The `Update` method of the <xref:System.Data.Common.DataAdapter> is called to resolve changes from a <xref:System.Data.DataSet> back to the data source.</span></span> <span data-ttu-id="2e89e-105">Als Argumente akzeptiert die `Update`-Methode, genau wie die `Fill`-Methode, eine Instanz eines `DataSet` sowie ein optionales <xref:System.Data.DataTable>-Objekt oder einen `DataTable`-Namen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-105">The `Update` method, like the `Fill` method, takes as arguments an instance of a `DataSet`, and an optional <xref:System.Data.DataTable> object or `DataTable` name.</span></span> <span data-ttu-id="2e89e-106">Die `DataSet`-Instanz ist das `DataSet`, das die vorgenommenen Änderungen enthält, und der `DataTable`-Wert gibt die Tabelle an, aus der die Änderungen abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-106">The `DataSet` instance is the `DataSet` that contains the changes that have been made, and the `DataTable` identifies the table from which to retrieve the changes.</span></span> <span data-ttu-id="2e89e-107">Wenn keine `DataTable` angegeben ist, wird die erste `DataTable` im `DataSet` verwendet.</span><span class="sxs-lookup"><span data-stu-id="2e89e-107">If no `DataTable` is specified, the first `DataTable` in the `DataSet` is used.</span></span>

<span data-ttu-id="2e89e-108">Wenn die `Update`-Methode aufgerufen wird, analysiert der `DataAdapter` die vorgenommenen Änderungen und führt dann den entsprechenden Befehl (INSERT, UPDATE oder DELETE) aus.</span><span class="sxs-lookup"><span data-stu-id="2e89e-108">When you call the `Update` method, the `DataAdapter` analyzes the changes that have been made and executes the appropriate command (INSERT, UPDATE, or DELETE).</span></span> <span data-ttu-id="2e89e-109">Wenn der `DataAdapter` eine Änderung an einer <xref:System.Data.DataRow> feststellt, verwendet er zum Verarbeiten der Änderung den <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, den <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> oder den <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e89e-109">When the `DataAdapter` encounters a change to a <xref:System.Data.DataRow>, it uses the <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A>, <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A>, or <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> to process the change.</span></span> <span data-ttu-id="2e89e-110">Dies gibt Ihnen die Gelegenheit, die Leistung der ADO.NET-Anwendung zu optimieren, indem Sie in der Entwurfsphase eine Befehlssyntax festlegen und, sofern möglich, gespeicherte Prozeduren verwenden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-110">This allows you to maximize the performance of your ADO.NET application by specifying command syntax at design time and, where possible, through the use of stored procedures.</span></span> <span data-ttu-id="2e89e-111">Sie müssen die Befehle vor dem Aufrufen von `Update` explizit festlegen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-111">You must explicitly set the commands before calling `Update`.</span></span> <span data-ttu-id="2e89e-112">Wenn `Update` aufgerufen wird und der entsprechende Befehl für ein bestimmtes Update nicht vorhanden ist (wenn z. B. `DeleteCommand` für gelöschte Zeilen fehlt), wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="2e89e-112">If `Update` is called and the appropriate command does not exist for a particular update (for example, no `DeleteCommand` for deleted rows), an exception is thrown.</span></span>

> [!NOTE]
> <span data-ttu-id="2e89e-113">Wenn Sie zum Bearbeiten oder Löschen von Daten mit einem `DataAdapter` gespeicherte SQL Server-Prozeduren verwenden, müssen Sie sicherstellen, dass in der Definition der gespeicherten Prozedur nicht SET NOCOUNT ON verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2e89e-113">If you are using SQL Server stored procedures to edit or delete data using a `DataAdapter`, make sure that you do not use SET NOCOUNT ON in the stored procedure definition.</span></span> <span data-ttu-id="2e89e-114">Anderenfalls ist die zurückgegebene Anzahl der betroffenen Zeilen gleich Null (0), was der `DataAdapter` als Parallelitätskonflikt interpretiert.</span><span class="sxs-lookup"><span data-stu-id="2e89e-114">This causes the rows affected count returned to be zero, which the `DataAdapter` interprets as a concurrency conflict.</span></span> <span data-ttu-id="2e89e-115">In diesem Fall wird eine <xref:System.Data.DBConcurrencyException> ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="2e89e-115">In this event, a <xref:System.Data.DBConcurrencyException> will be thrown.</span></span>

<span data-ttu-id="2e89e-116">Command-Parameter können verwendet werden, um Ein- und Ausgabewerte für eine SQL-Anweisung oder eine gespeicherte Prozedur für jede geänderte Zeile in einem `DataSet` anzugeben.</span><span class="sxs-lookup"><span data-stu-id="2e89e-116">Command parameters can be used to specify input and output values for an SQL statement or stored procedure for each modified row in a `DataSet`.</span></span> <span data-ttu-id="2e89e-117">Weitere Informationen finden Sie unter [DataAdapter-Parameter](dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="2e89e-117">For more information, see [DataAdapter Parameters](dataadapter-parameters.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2e89e-118">Wichtig ist dabei, zwischen dem Löschen einer Zeile in einer <xref:System.Data.DataTable> und dem Entfernen der Zeile zu unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-118">It is important to understand the difference between deleting a row in a <xref:System.Data.DataTable> and removing the row.</span></span> <span data-ttu-id="2e89e-119">Wenn Sie die `Remove`-Methode oder die `RemoveAt`-Methode aufrufen, wird die Zeile sofort entfernt.</span><span class="sxs-lookup"><span data-stu-id="2e89e-119">When you call the `Remove` or `RemoveAt` method, the row is removed immediately.</span></span> <span data-ttu-id="2e89e-120">Wenn Sie anschließend die `DataTable` oder das `DataSet` an einen `DataAdapter` übergeben und `Update` aufrufen, bleiben die entsprechenden Zeilen in der Datenquelle unangetastet.</span><span class="sxs-lookup"><span data-stu-id="2e89e-120">Any corresponding rows in the back end data source will not be affected if you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`.</span></span> <span data-ttu-id="2e89e-121">Wenn Sie die Methode `Delete` verwenden, bleibt die Zeile in der `DataTable` erhalten, wird aber als zu löschen markiert.</span><span class="sxs-lookup"><span data-stu-id="2e89e-121">When you use the `Delete` method, the row remains in the `DataTable` and is marked for deletion.</span></span> <span data-ttu-id="2e89e-122">Das anschließende Übergeben der `DataTable` oder des `DataSet` an einen `DataAdapter` und das Aufrufen von `Update` führt dazu, dass die entsprechende Zeile in der Datenquelle gelöscht wird.</span><span class="sxs-lookup"><span data-stu-id="2e89e-122">If you then pass the `DataTable` or `DataSet` to a `DataAdapter` and call `Update`, the corresponding row in the back end data source is deleted.</span></span>

<span data-ttu-id="2e89e-123">Wenn Ihre `DataTable` einer einzelnen Datenbanktabelle zugeordnet ist oder aus einer einzelnen Datenbanktabelle generiert wurde, können Sie mithilfe des <xref:System.Data.Common.DbCommandBuilder>-Objekts automatisch das `DeleteCommand`-, das `InsertCommand`- und das `UpdateCommand`-Objekt für den `DataAdapter` generieren.</span><span class="sxs-lookup"><span data-stu-id="2e89e-123">If your `DataTable` maps to or is generated from a single database table, you can take advantage of the <xref:System.Data.Common.DbCommandBuilder> object to automatically generate the `DeleteCommand`, `InsertCommand`, and `UpdateCommand` objects for the `DataAdapter`.</span></span> <span data-ttu-id="2e89e-124">Weitere Informationen finden Sie unter [Erstellen von Befehlen mit CommandBuilder](generating-commands-with-commandbuilders.md).</span><span class="sxs-lookup"><span data-stu-id="2e89e-124">For more information, see [Generating Commands with CommandBuilders](generating-commands-with-commandbuilders.md).</span></span>

## <a name="using-updatedrowsource-to-map-values-to-a-dataset"></a><span data-ttu-id="2e89e-125">Verwenden von "UpdatedRowSource" zum Zuordnen von Werten zu einem "DataSet"</span><span class="sxs-lookup"><span data-stu-id="2e89e-125">Using UpdatedRowSource to Map Values to a DataSet</span></span>

<span data-ttu-id="2e89e-126">Mit der -Eigenschaft eines -Objekts können Sie steuern, wie die von der Datenquelle zurückgegebenen Werte nach einem Aufruf der Update-Methode eines  der  erneut zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-126">You can control how the values returned from the data source are mapped back to the `DataTable` following a call to the Update method of a `DataAdapter`, by using the <xref:System.Data.Common.DbCommand.UpdatedRowSource%2A> property of a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="2e89e-127">Durch Festlegen eines der `UpdatedRowSource`-Enumerationswerte für die <xref:System.Data.UpdateRowSource>-Eigenschaft kann gesteuert werden, ob die von den `DataAdapter`-Befehlen zurückgegebenen Ausgabeparameter ignoriert oder auf die geänderte Zeile im `DataSet` angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-127">By setting the `UpdatedRowSource` property to one of the <xref:System.Data.UpdateRowSource> enumeration values, you can control whether output parameters returned by the `DataAdapter` commands are ignored or applied to the changed row in the `DataSet`.</span></span> <span data-ttu-id="2e89e-128">Es kann auch festgelegt werden, ob die erste zurückgegebene Zeile (wenn vorhanden) auf die geänderte Zeile in der `DataTable` angewendet wird.</span><span class="sxs-lookup"><span data-stu-id="2e89e-128">You can also specify whether the first returned row (if it exists) is applied to the changed row in the `DataTable`.</span></span>

<span data-ttu-id="2e89e-129">In der folgenden Tabelle werden die verschiedenen Werte der `UpdateRowSource`-Enumeration und deren Auswirkungen auf das Verhalten eines mit einem `DataAdapter` verwendeten Befehls beschrieben.</span><span class="sxs-lookup"><span data-stu-id="2e89e-129">The following table describes the different values of the `UpdateRowSource` enumeration and how they affect the behavior of a command used with a `DataAdapter`.</span></span>

|<span data-ttu-id="2e89e-130">"UpdatedRowSource"-Enumeration</span><span class="sxs-lookup"><span data-stu-id="2e89e-130">UpdatedRowSource Enumeration</span></span>|<span data-ttu-id="2e89e-131">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2e89e-131">Description</span></span>|
|----------------------------------|-----------------|
|<xref:System.Data.UpdateRowSource.Both>|<span data-ttu-id="2e89e-132">Sowohl die Ausgabeparameter als auch die erste Zeile eines zurückgegebenen Resultset können der geänderten Zeile im `DataSet` zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-132">Both the output parameters and the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.FirstReturnedRecord>|<span data-ttu-id="2e89e-133">Nur die Daten in der ersten Zeile eines zurückgegebenen Resultset können der geänderten Zeile im `DataSet` zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-133">Only the data in the first row of a returned result set may be mapped to the changed row in the `DataSet`.</span></span>|
|<xref:System.Data.UpdateRowSource.None>|<span data-ttu-id="2e89e-134">Alle Ausgabeparameter oder Zeilen eines zurückgegebenen Resultset werden ignoriert.</span><span class="sxs-lookup"><span data-stu-id="2e89e-134">Any output parameters or rows of a returned result set are ignored.</span></span>|
|<xref:System.Data.UpdateRowSource.OutputParameters>|<span data-ttu-id="2e89e-135">Der geänderten Zeile im `DataSet` können nur Ausgabeparameter zugeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-135">Only output parameters may be mapped to the changed row in the `DataSet`.</span></span>|

<span data-ttu-id="2e89e-136">Die `Update`-Methode aktualisiert die Datenquelle mit den vorgenommenen Änderungen. Die Daten in der Datenquelle können aber seit dem letzten Füllen des `DataSet` durch andere Clients geändert worden sein.</span><span class="sxs-lookup"><span data-stu-id="2e89e-136">The `Update` method resolves your changes back to the data source; however other clients may have modified data at the data source since the last time you filled the `DataSet`.</span></span> <span data-ttu-id="2e89e-137">Wenn Sie das `DataSet` mit den aktuellen Daten aktualisieren möchten, verwenden Sie den `DataAdapter` und die `Fill`-Methode.</span><span class="sxs-lookup"><span data-stu-id="2e89e-137">To refresh your `DataSet` with current data, use the `DataAdapter` and `Fill` method.</span></span> <span data-ttu-id="2e89e-138">Der Tabelle werden neue Zeilen hinzugefügt, und aktualisierte Informationen werden in die vorhandenen Zeilen eingefügt.</span><span class="sxs-lookup"><span data-stu-id="2e89e-138">New rows will be added to the table, and updated information will be incorporated into existing rows.</span></span> <span data-ttu-id="2e89e-139">Die `Fill`-Methode überprüft die Primärschlüsselwerte der Zeilen im `DataSet` und der vom `SelectCommand` zurückgegebenen Zeilen und bestimmt so, ob eine neue Zeile hinzugefügt oder die bestehende Zeile aktualisiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="2e89e-139">The `Fill` method determines whether a new row will be added or an existing row will be updated by examining the primary key values of the rows in the `DataSet` and the rows returned by the `SelectCommand`.</span></span> <span data-ttu-id="2e89e-140">Wenn die `Fill`-Methode einen Primärschlüsselwert für eine Zeile im `DataSet` findet, der mit einem Primärschlüsselwert einer Zeile in den vom `SelectCommand` zurückgegebenen Ergebnissen übereinstimmt, aktualisiert sie die vorhandene Zeile mit den Informationen aus der vom `SelectCommand` zurückgegebenen Zeile und legt den <xref:System.Data.DataRow.RowState%2A> der vorhandenen Zeile auf `Unchanged` fest.</span><span class="sxs-lookup"><span data-stu-id="2e89e-140">If the `Fill` method encounters a primary key value for a row in the `DataSet` that matches a primary key value from a row in the results returned by the `SelectCommand`, it updates the existing row with the information from the row returned by the `SelectCommand` and sets the <xref:System.Data.DataRow.RowState%2A> of the existing row to `Unchanged`.</span></span> <span data-ttu-id="2e89e-141">Wenn der Primärschlüsselwert einer vom `SelectCommand` zurückgegebenen Zeile keinem der Primärschlüsselwerte der Zeilen im `DataSet` entspricht, fügt die `Fill`-Methode eine neue Zeile mit dem `RowState``Unchanged` hinzu.</span><span class="sxs-lookup"><span data-stu-id="2e89e-141">If a row returned by the `SelectCommand` has a primary key value that does not match any of the primary key values of the rows in the `DataSet`, the `Fill` method adds a new row with a `RowState` of `Unchanged`.</span></span>

> [!NOTE]
> <span data-ttu-id="2e89e-142">Wenn der `SelectCommand` die Ergebnisse eines OUTER JOIN zurückgibt, legt der `DataAdapter` keinen `PrimaryKey`-Wert für die resultierende `DataTable` fest.</span><span class="sxs-lookup"><span data-stu-id="2e89e-142">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` will not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="2e89e-143">Sie müssen den `PrimaryKey` selbst definieren, um sicherzustellen, dass doppelte Zeilen ordnungsgemäß aufgelöst werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-143">You must define the `PrimaryKey` yourself to ensure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="2e89e-144">Weitere Informationen finden Sie unter [Definieren von primär Schlüsseln](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="2e89e-144">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>

<span data-ttu-id="2e89e-145">Um Ausnahmen zu behandeln, die beim Aufrufen der-Methode auftreten können `Update` , können Sie das-Ereignis verwenden, `RowUpdated` um auf Fehler beim Aktualisieren von Zeilen zu reagieren (siehe [Handling DataAdapter-Ereignisse](handling-dataadapter-events.md)), oder Sie können auf festlegen, `DataAdapter.ContinueUpdateOnError` bevor Sie `true` aufrufen `Update` , und auf die in der-Eigenschaft einer bestimmten Zeile gespeicherten Fehlerinformationen reagieren, `RowError` Wenn das Update fertig ist (siehe [Zeilen Fehlerinformationen](./dataset-datatable-dataview/row-error-information.md)).</span><span class="sxs-lookup"><span data-stu-id="2e89e-145">To handle exceptions that may occur when calling the `Update` method, you can use the `RowUpdated` event to respond to row update errors as they occur (see [Handling DataAdapter Events](handling-dataadapter-events.md)), or you can set `DataAdapter.ContinueUpdateOnError` to `true` before calling `Update`, and respond to the error information stored in the `RowError` property of a particular row when the update is complete (see [Row Error Information](./dataset-datatable-dataview/row-error-information.md)).</span></span>

> [!NOTE]
> <span data-ttu-id="2e89e-146">`AcceptChanges` `DataSet` Wenn Sie für, oder aufrufen, werden `DataTable` `DataRow` alle `Original` Werte für ein `DataRow` mit den `Current` Werten für die überschrieben `DataRow` .</span><span class="sxs-lookup"><span data-stu-id="2e89e-146">Calling `AcceptChanges` on the `DataSet`, `DataTable`, or `DataRow` will cause all `Original` values for a `DataRow` to be overwritten with the `Current` values for the `DataRow`.</span></span> <span data-ttu-id="2e89e-147">Wenn die Feldwerte, mit denen die Zeile als eindeutig identifiziert wird, geändert wurden, stimmen die `AcceptChanges`-Werte nicht mehr mit den Werten in der Datenquelle überein, nachdem `Original` aufgerufen wurde.</span><span class="sxs-lookup"><span data-stu-id="2e89e-147">If the field values that identify the row as unique have been modified, after calling `AcceptChanges` the `Original` values will no longer match the values in the data source.</span></span> <span data-ttu-id="2e89e-148">`AcceptChanges` wird während eines Aufrufs der Update-Methode eines `DataAdapter` automatisch für jede Zeile aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-148">`AcceptChanges` is called automatically for each row during a call to the Update method of a `DataAdapter`.</span></span> <span data-ttu-id="2e89e-149">Sie können die Originalwerte während eines Aufrufs der Update-Methode beibehalten, indem Sie zuerst die -Eigenschaft des  auf false setzen oder indem Sie einen Ereignishandler für das -Ereignis erstellen und den  auf  festlegen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-149">You can preserve the original values during a call to the Update method by first setting the `AcceptChangesDuringUpdate` property of the `DataAdapter` to false, or by creating an event handler for the `RowUpdated` event and setting the <xref:System.Data.Common.RowUpdatedEventArgs.Status%2A> to <xref:System.Data.UpdateStatus.SkipCurrentRow>.</span></span> <span data-ttu-id="2e89e-150">Weitere Informationen finden Sie unter Zusammenführen von [DataSet-Inhalten](./dataset-datatable-dataview/merging-dataset-contents.md) und [Verarbeiten von DataAdapter-Ereignissen](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="2e89e-150">For more information, see [Merging DataSet Contents](./dataset-datatable-dataview/merging-dataset-contents.md) and [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>

## <a name="example"></a><span data-ttu-id="2e89e-151">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2e89e-151">Example</span></span>

<span data-ttu-id="2e89e-152">In den folgenden Beispielen wird veranschaulicht, wie Updates für geänderte Zeilen durch explizites Festlegen des `UpdateCommand` von `DataAdapter` und durch Aufrufen der-Methode durchgeführt werden `Update` .</span><span class="sxs-lookup"><span data-stu-id="2e89e-152">The following examples demonstrate how to perform updates to modified rows by explicitly setting the `UpdateCommand` of a `DataAdapter` and calling its `Update` method.</span></span> <span data-ttu-id="2e89e-153">Beachten Sie, dass der in der WHERE-Klausel der UPDATE-Anweisung festgelegte Parameterwert angibt, dass der `Original`-Wert der `SourceColumn` verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2e89e-153">Notice that the parameter specified in the WHERE clause of the UPDATE statement is set to use the `Original` value of the `SourceColumn`.</span></span> <span data-ttu-id="2e89e-154">Dies ist wichtig, weil der `Current`-Wert möglicherweise geändert wurde und u. U. nicht mehr mit dem Wert in der Datenquelle übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="2e89e-154">This is important, because the `Current` value may have been modified and may not match the value in the data source.</span></span> <span data-ttu-id="2e89e-155">Beim `Original`-Wert handelt es sich um den Wert, mit dem die `DataTable` aus der Datenquelle aufgefüllt wurde.</span><span class="sxs-lookup"><span data-stu-id="2e89e-155">The `Original` value is the value that was used to populate the `DataTable` from the data source.</span></span>

[!code-csharp[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/CS/source.cs#1)]
[!code-vb[DataWorks SqlClient.DataAdapterUpdate#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.DataAdapterUpdate/VB/source.vb#1)]

## <a name="autoincrement-columns"></a><span data-ttu-id="2e89e-156">"AutoIncrement"-Spalten</span><span class="sxs-lookup"><span data-stu-id="2e89e-156">AutoIncrement Columns</span></span>

<span data-ttu-id="2e89e-157">Wenn die Tabellen aus der Datenquelle automatisch inkrementierende Spalten besitzen, können Sie die Spalten im `DataSet` füllen. Geben Sie dazu die automatisch inkrementierenden Werte als Ausgabeparameter einer gespeicherten Prozedur zurück, und ordnen Sie diesen Parameter einer Spalte in einer Tabelle zu, indem Sie den automatisch inkrementierenden Wert in der ersten Zeile eines von einer gespeicherten Prozedur oder einer SQL-Anweisung zurückgegebenen Resultset zurückgeben oder indem Sie das `RowUpdated`-Ereignis des `DataAdapter` verwenden, um eine weitere SELECT-Anweisung auszuführen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-157">If the tables from your data source have auto-incrementing columns, you can fill the columns in your `DataSet` either by returning the auto-increment value as an output parameter of a stored procedure and mapping that to a column in a table, by returning the auto-increment value in the first row of a result set returned by a stored procedure or SQL statement, or by using the `RowUpdated` event of the `DataAdapter` to execute an additional SELECT statement.</span></span> <span data-ttu-id="2e89e-158">Weitere Informationen und ein Beispiel finden Sie unter [Abrufen von Identitäts-oder](retrieving-identity-or-autonumber-values.md)Auto Sequenz Werten.</span><span class="sxs-lookup"><span data-stu-id="2e89e-158">For more information and an example, see [Retrieving Identity or Autonumber Values](retrieving-identity-or-autonumber-values.md).</span></span>

## <a name="ordering-of-inserts-updates-and-deletes"></a><span data-ttu-id="2e89e-159">Reihenfolge von Einfüge-, Update- und Löschvorgängen</span><span class="sxs-lookup"><span data-stu-id="2e89e-159">Ordering of Inserts, Updates, and Deletes</span></span>

<span data-ttu-id="2e89e-160">In vielen Fällen ist die Reihenfolge, in der die am `DataSet` vorgenommenen Änderungen zur Datenquelle gesendet werden, sehr wichtig.</span><span class="sxs-lookup"><span data-stu-id="2e89e-160">In many circumstances, the order in which changes made through the `DataSet` are sent to the data source is important.</span></span> <span data-ttu-id="2e89e-161">Wenn beispielsweise ein Primärschlüsselwert für eine vorhandene Zeile aktualisiert und eine neue Zeile mit dem neuen Primärschlüsselwert als Fremdschlüssel hinzugefügt wurde, muss das Update vor der Einfügung verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-161">For example, if a primary key value for an existing row is updated, and a new row has been added with the new primary key value as a foreign key, it is important to process the update before the insert.</span></span>

<span data-ttu-id="2e89e-162">Mithilfe der `Select`-Methode der `DataTable` können Sie ein `DataRow`-Array zurückgeben, das nur auf Zeilen mit einem bestimmten `RowState` verweist.</span><span class="sxs-lookup"><span data-stu-id="2e89e-162">You can use the `Select` method of the `DataTable` to return a `DataRow` array that only references rows with a particular `RowState`.</span></span> <span data-ttu-id="2e89e-163">Anschließend können Sie das zurückgegebene `DataRow`-Array an die `Update`-Methode des `DataAdapter` übergeben, damit die geänderten Zeilen verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-163">You can then pass the returned `DataRow` array to the `Update` method of the `DataAdapter` to process the modified rows.</span></span> <span data-ttu-id="2e89e-164">Wenn Sie eine Teilmenge von Zeilen angeben, die aktualisiert werden sollen, können Sie die Reihenfolge steuern, in der Einfügungen, Updates und Löschvorgänge verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="2e89e-164">By specifying a subset of rows to be updated, you can control the order in which inserts, updates, and deletes are processed.</span></span>

## <a name="example"></a><span data-ttu-id="2e89e-165">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2e89e-165">Example</span></span>

<span data-ttu-id="2e89e-166">Durch den folgenden Code wird beispielsweise sichergestellt, dass die gelöschten Zeilen der Tabelle zuerst verarbeitet werden, anschließend die aktualisierten Zeilen und dann die eingefügten Zeilen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-166">For example, the following code ensures that the deleted rows of the table are processed first, then the updated rows, and then the inserted rows.</span></span>

```vb
Dim table As DataTable = dataSet.Tables("Customers")

' First process deletes.
dataSet.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Deleted))

' Next process updates.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.ModifiedCurrent))

' Finally, process inserts.
adapter.Update(table.Select(Nothing, Nothing, _
  DataViewRowState.Added))
```

```csharp
DataTable table = dataSet.Tables["Customers"];

// First process deletes.
adapter.Update(table.Select(null, null, DataViewRowState.Deleted));

// Next process updates.
adapter.Update(table.Select(null, null,
  DataViewRowState.ModifiedCurrent));

// Finally, process inserts.
adapter.Update(table.Select(null, null, DataViewRowState.Added));
```

## <a name="use-a-dataadapter-to-retrieve-and-update-data"></a><span data-ttu-id="2e89e-167">Verwenden von "DataAdapter" zum Abrufen und Aktualisieren von Daten</span><span class="sxs-lookup"><span data-stu-id="2e89e-167">Use a DataAdapter to Retrieve and Update Data</span></span>

<span data-ttu-id="2e89e-168">Sie können DataAdapter verwenden, um die Daten abzurufen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="2e89e-168">You can use a DataAdapter to retrieve and update the data.</span></span>

- <span data-ttu-id="2e89e-169">Im Beispiel wird DataAdapter.AcceptChangesDuringFill verwendet, um die Daten in der Datenbank zu klonen.</span><span class="sxs-lookup"><span data-stu-id="2e89e-169">The sample uses DataAdapter.AcceptChangesDuringFill to clone the data in the database.</span></span> <span data-ttu-id="2e89e-170">Wenn die Eigenschaft auf False festgelegt ist, wird AcceptChanges beim Auffüllen der Datenbank nicht aufgerufen, und die neu hinzugefügten Zeilen werden als eingefügte Zeilen behandelt.</span><span class="sxs-lookup"><span data-stu-id="2e89e-170">If the property is set as false, AcceptChanges is not called when filling the table, and the newly added rows are treated as inserted rows.</span></span> <span data-ttu-id="2e89e-171">Daher werden im Beispiel diese Zeilen zum Einfügen der neuen Zeilen in die Datenbank verwendet.</span><span class="sxs-lookup"><span data-stu-id="2e89e-171">So, the sample uses these rows to insert the new rows into the database.</span></span>

- <span data-ttu-id="2e89e-172">In den Beispielen wird DataAdapter.TableMappings verwendet, um die Zuordnung zwischen der Quelltabelle und der DataTable zu definieren.</span><span class="sxs-lookup"><span data-stu-id="2e89e-172">The samples uses DataAdapter.TableMappings to define the mapping between the source table and DataTable.</span></span>

- <span data-ttu-id="2e89e-173">Im Beispiel wird DataAdapter.FillLoadOption verwendet, um zu bestimmen, wie die DataTable aus DbDataReader vom Adapter aufgefüllt wird.</span><span class="sxs-lookup"><span data-stu-id="2e89e-173">The sample uses DataAdapter.FillLoadOption to determine how the adapter fills the DataTable from the DbDataReader.</span></span> <span data-ttu-id="2e89e-174">Beim Erstellen einer DataTable können die Daten aus der Datenbank nur in die aktuelle oder ursprüngliche Version geschrieben werden, wenn die Eigenschaft auf LoadOption.Upsert oder LoadOption.PreserveChanges festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="2e89e-174">When you create a DataTable, you can only write the data from database to the current version or the original version by setting the property as the LoadOption.Upsert or the LoadOption.PreserveChanges.</span></span>

- <span data-ttu-id="2e89e-175">Im Beispiel wird die Tabelle auch mithilfe von DbDataAdapter.UpdateBatchSize zum Ausführen von Batchvorgängen aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="2e89e-175">The sample will also update the table by using DbDataAdapter.UpdateBatchSize to perform batch operations.</span></span>

<span data-ttu-id="2e89e-176">Bevor Sie dieses Beispiel kompilieren und ausführen, müssen Sie die Beispieldatenbank erstellen:</span><span class="sxs-lookup"><span data-stu-id="2e89e-176">Before you compile and run the sample, you need to create the sample database:</span></span>

```sql
USE [master]
GO

CREATE DATABASE [MySchool]

GO

USE [MySchool]
GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Course]([CourseID] [nvarchar](10) NOT NULL,
[Year] [smallint] NOT NULL,
[Title] [nvarchar](100) NOT NULL,
[Credits] [int] NOT NULL,
[DepartmentID] [int] NOT NULL,
 CONSTRAINT [PK_Course] PRIMARY KEY CLUSTERED
(
[CourseID] ASC,
[Year] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Department]([DepartmentID] [int] IDENTITY(1,1) NOT NULL,
[Name] [nvarchar](50) NOT NULL,
[Budget] [money] NOT NULL,
[StartDate] [datetime] NOT NULL,
[Administrator] [int] NULL,
 CONSTRAINT [PK_Department] PRIMARY KEY CLUSTERED
(
[DepartmentID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON) ON [PRIMARY]) ON [PRIMARY]

GO

INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1045', 2012, N'Calculus', 4, 7)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C1061', 2012, N'Physics', 4, 1)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2021', 2012, N'Composition', 3, 2)
INSERT [dbo].[Course] ([CourseID], [Year], [Title], [Credits], [DepartmentID]) VALUES (N'C2042', 2012, N'Literature', 4, 2)

SET IDENTITY_INSERT [dbo].[Department] ON

INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (1, N'Engineering', 350000.0000, CAST(0x0000999C00000000 AS DateTime), 2)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (2, N'English', 120000.0000, CAST(0x0000999C00000000 AS DateTime), 6)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (4, N'Economics', 200000.0000, CAST(0x0000999C00000000 AS DateTime), 4)
INSERT [dbo].[Department] ([DepartmentID], [Name], [Budget], [StartDate], [Administrator]) VALUES (7, N'Mathematics', 250024.0000, CAST(0x0000999C00000000 AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Department] OFF

ALTER TABLE [dbo].[Course]  WITH CHECK ADD  CONSTRAINT [FK_Course_Department] FOREIGN KEY([DepartmentID])
REFERENCES [dbo].[Department] ([DepartmentID])
GO
ALTER TABLE [dbo].[Course] CHECK CONSTRAINT [FK_Course_Department]
GO
```

<span data-ttu-id="2e89e-177">C#-und Visual Basic Projekte mit diesem Codebeispiel finden Sie unter [Codebeispiele für Entwickler](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span><span class="sxs-lookup"><span data-stu-id="2e89e-177">C# and Visual Basic projects with this code sample can be found on [Developer Code Samples](https://code.msdn.microsoft.com/site/search?f%5B0%5D.Type=SearchText&f%5B0%5D.Value=How%20to%20use%20DataAdapter%20to%20retrieve%20and%20update%20data&f%5B1%5D).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.SqlClient;
using System.Linq;
using CSDataAdapterOperations.Properties;

namespace CSDataAdapterOperations.Properties {
   internal sealed partial class Settings : global::System.Configuration.ApplicationSettingsBase {

      private static Settings defaultInstance = ((Settings)(global::System.Configuration.ApplicationSettingsBase.Synchronized(new Settings())));

      public static Settings Default {
         get {
            return defaultInstance;
         }
      }

      [global::System.Configuration.ApplicationScopedSettingAttribute()]
      [global::System.Configuration.DefaultSettingValueAttribute("Data Source=(local);Initial Catalog=MySchool;Integrated Security=True")]
      public string MySchoolConnectionString {
         get {
            return ((string)(this["MySchoolConnectionString"]));
         }
      }
   }
}

class Program {
   static void Main(string[] args) {
      Settings settings = new Settings();

      // Copy the data from the database.  Get the table Department and Course from the database.
      String selectString = @"SELECT [DepartmentID],[Name],[Budget],[StartDate],[Administrator]
                                     FROM [MySchool].[dbo].[Department];

                                   SELECT [CourseID],@Year as [Year],Max([Title]) as [Title],
                                   Max([Credits]) as [Credits],Max([DepartmentID]) as [DepartmentID]
                                   FROM [MySchool].[dbo].[Course]
                                   Group by [CourseID]";

      DataSet mySchool = new DataSet();

      SqlCommand selectCommand = new SqlCommand(selectString);
      SqlParameter parameter = selectCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2);
      parameter.Value = new Random(DateTime.Now.Millisecond).Next(9999);

      // Use DataTableMapping to map the source tables and the destination tables.
      DataTableMapping[] tableMappings = {new DataTableMapping("Table", "Department"), new DataTableMapping("Table1", "Course")};
      CopyData(mySchool, settings.MySchoolConnectionString, selectCommand, tableMappings);

      Console.WriteLine("The following tables are from the database.");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      // Roll back the changes
      DataTable department = mySchool.Tables["Department"];
      DataTable course = mySchool.Tables["Course"];

      department.Rows[0]["Name"] = "New" + department.Rows[0][1];
      course.Rows[0]["Title"] = "New" + course.Rows[0]["Title"];
      course.Rows[0]["Credits"] = 10;

      Console.WriteLine("After we changed the tables:");
      foreach (DataTable table in mySchool.Tables) {
         Console.WriteLine(table.TableName);
         ShowDataTable(table);
      }

      department.RejectChanges();
      Console.WriteLine("After use the RejectChanges method in Department table to roll back the changes:");
      ShowDataTable(department);

      DataColumn[] primaryColumns = { course.Columns["CourseID"] };
      DataColumn[] resetColumns = { course.Columns["Title"] };
      ResetCourse(course, settings.MySchoolConnectionString, primaryColumns, resetColumns);
      Console.WriteLine("After use the ResetCourse method in Course table to roll back the changes:");
      ShowDataTable(course);

      // Batch update the table.
      String insertString = @"Insert into [MySchool].[dbo].[Course]([CourseID],[Year],[Title],
                                   [Credits],[DepartmentID])
             values (@CourseID,@Year,@Title,@Credits,@DepartmentID)";
      SqlCommand insertCommand = new SqlCommand(insertString);
      insertCommand.Parameters.Add("@CourseID", SqlDbType.NVarChar, 10, "CourseID");
      insertCommand.Parameters.Add("@Year", SqlDbType.SmallInt, 2, "Year");
      insertCommand.Parameters.Add("@Title", SqlDbType.NVarChar, 100, "Title");
      insertCommand.Parameters.Add("@Credits", SqlDbType.Int, 4, "Credits");
      insertCommand.Parameters.Add("@DepartmentID", SqlDbType.Int, 4, "DepartmentID");

      const Int32 batchSize = 10;
      BatchInsertUpdate(course, settings.MySchoolConnectionString, insertCommand, batchSize);
   }

   private static void CopyData(DataSet dataSet, String connectionString, SqlCommand selectCommand, DataTableMapping[] tableMappings) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {adapter.TableMappings.AddRange(tableMappings);
            // If set the AcceptChangesDuringFill as the false, AcceptChanges will not be called on a
            // DataRow after it is added to the DataTable during any of the Fill operations.
            adapter.AcceptChangesDuringFill = false;

            adapter.Fill(dataSet);
         }
      }
   }

   // Roll back only one column or several columns data of the Course table by call ResetDataTable method.
   private static void ResetCourse(DataTable table, String connectionString,
       DataColumn[] primaryColumns, DataColumn[] resetColumns) {
      table.PrimaryKey = primaryColumns;

      // Build the query string
      String primaryCols = String.Join(",", primaryColumns.Select(col => col.ColumnName));
      String resetCols = String.Join(",", resetColumns.Select(col => $"Max({col.ColumnName}) as {col.ColumnName}"));

      String selectString = $"Select {primaryCols},{resetCols} from Course Group by {primaryCols}");

      SqlCommand selectCommand = new SqlCommand(selectString);

      ResetDataTable(table, connectionString, selectCommand);
   }

   // RejectChanges will roll back all changes made to the table since it was loaded, or the last time AcceptChanges
   // was called. When you copy from the database, you can lose all the data after calling RejectChanges
   // The ResetDataTable method rolls back one or more columns of data.
   private static void ResetDataTable(DataTable table, String connectionString,
       SqlCommand selectCommand) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         selectCommand.Connection = connection;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter(selectCommand)) {
            // The incoming values for this row will be written to the current version of each
            // column. The original version of each column's data will not be changed.
            adapter.FillLoadOption = LoadOption.Upsert;

            adapter.Fill(table);
         }
      }
   }

   private static void BatchInsertUpdate(DataTable table, String connectionString,
       SqlCommand insertCommand, Int32 batchSize) {
      using (SqlConnection connection = new SqlConnection(connectionString)) {
         insertCommand.Connection = connection;
         // When setting UpdateBatchSize to a value other than 1, all the commands
         // associated with the SqlDataAdapter have to have their UpdatedRowSource
         // property set to None or OutputParameters. An exception is thrown otherwise.
         insertCommand.UpdatedRowSource = UpdateRowSource.None;

         connection.Open();

         using (SqlDataAdapter adapter = new SqlDataAdapter()) {
            adapter.InsertCommand = insertCommand;
            // Gets or sets the number of rows that are processed in each round-trip to the server.
            // Setting it to 1 disables batch updates, as rows are sent one at a time.
            adapter.UpdateBatchSize = batchSize;

            adapter.Update(table);

            Console.WriteLine("Successfully to update the table.");
         }
      }
   }

   private static void ShowDataTable(DataTable table) {
      foreach (DataColumn col in table.Columns) {
         Console.Write("{0,-14}", col.ColumnName);
      }
      Console.WriteLine("{0,-14}", "RowState");

      foreach (DataRow row in table.Rows) {
         foreach (DataColumn col in table.Columns) {
            if (col.DataType.Equals(typeof(DateTime)))
               Console.Write("{0,-14:d}", row[col]);
            else if (col.DataType.Equals(typeof(Decimal)))
               Console.Write("{0,-14:C}", row[col]);
            else
               Console.Write("{0,-14}", row[col]);
         }
         Console.WriteLine("{0,-14}", row.RowState);
      }
   }
}
```

## <a name="see-also"></a><span data-ttu-id="2e89e-178">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2e89e-178">See also</span></span>

- [<span data-ttu-id="2e89e-179">"DataAdapters" und "DataReaders"</span><span class="sxs-lookup"><span data-stu-id="2e89e-179">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="2e89e-180">Zeilenstatus und Zeilenversionen</span><span class="sxs-lookup"><span data-stu-id="2e89e-180">Row States and Row Versions</span></span>](./dataset-datatable-dataview/row-states-and-row-versions.md)
- [<span data-ttu-id="2e89e-181">"AcceptChanges" und "RejectChanges"</span><span class="sxs-lookup"><span data-stu-id="2e89e-181">AcceptChanges and RejectChanges</span></span>](./dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)
- [<span data-ttu-id="2e89e-182">Zusammenführen von DataSet-Inhalten</span><span class="sxs-lookup"><span data-stu-id="2e89e-182">Merging DataSet Contents</span></span>](./dataset-datatable-dataview/merging-dataset-contents.md)
- [<span data-ttu-id="2e89e-183">Abrufen von Identity- oder Autonumber-Werten</span><span class="sxs-lookup"><span data-stu-id="2e89e-183">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)
- [<span data-ttu-id="2e89e-184">Übersicht über ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2e89e-184">ADO.NET Overview</span></span>](ado-net-overview.md)
