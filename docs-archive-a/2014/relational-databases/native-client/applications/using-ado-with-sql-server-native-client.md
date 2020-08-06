---
title: SQL Server Native Client | での ADO の使用Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, ADO
- data access [SQL Server Native Client], ADO
- ADO [SQL Server Native Client]
- SQLNCLI, ADO
ms.assetid: 118a7cac-4c0d-44fd-b63e-3d542932d239
author: rothja
ms.author: jroth
ms.openlocfilehash: ccd14432aa3541572467a4c651c1f48b1ac957f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738214"
---
# <a name="using-ado-with-sql-server-native-client"></a><span data-ttu-id="85615-102">SQL Server Native Client と ADO の併用</span><span class="sxs-lookup"><span data-stu-id="85615-102">Using ADO with SQL Server Native Client</span></span>
  <span data-ttu-id="85615-103">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]複数のアクティブな結果セット (MARS)、クエリ通知、ユーザー定義型 (udt)、または新しい**xml**データ型など、で導入された新機能を利用するには、ActiveX データオブジェクト (ADO) を使用する既存のアプリケーションで、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データアクセスプロバイダーとして Native Client OLE DB プロバイダーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85615-103">In order to take advantage of new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] such as multiple active result sets (MARS), query notifications, user-defined types (UDTs), or the new **xml** data type, existing applications that use ActiveX Data Objects (ADO) should use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider as their data access provider.</span></span>  
  
 <span data-ttu-id="85615-104">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の新機能を一切使用する必要がない場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用する必要はありません。つまり、現在のデータ アクセス プロバイダー (通常は SQLOLEDB) を継続して使用できます。</span><span class="sxs-lookup"><span data-stu-id="85615-104">If you do not need to use any of the new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], there is no need to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider; you can continue using your current data access provider, which is typically SQLOLEDB.</span></span> <span data-ttu-id="85615-105">既存のアプリケーションを強化して、[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] の新機能を使用する必要がある場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="85615-105">If you are enhancing an existing application and you need to use the new features introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], you should use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85615-106">新しいアプリケーションを開発している場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の最新バージョンのすべての新機能にアクセスできるように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ではなく、ADO.NET および .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の使用を検討することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="85615-106">If you are developing a new application, it is recommended that you consider using ADO.NET and the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instead of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to access all the new features of recent versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="85615-107">.NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の詳細については、ADO.NET に関する .NET Framework SDK のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="85615-107">For more information about the .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see the .NET Framework SDK documentation for ADO.NET.</span></span>  
  
 <span data-ttu-id="85615-108">ADO から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の最新バージョンの新機能を使用できるように、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを機能強化し、OLE DB の中核となる機能を拡張しました。</span><span class="sxs-lookup"><span data-stu-id="85615-108">To enable ADO to use new features of recent versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], some enhancements have been made to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider which extends the core features of OLE DB.</span></span> <span data-ttu-id="85615-109">ADO アプリケーションはこのような機能強化により、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の新しい機能、および [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] で導入された 2 つのデータ型 (**xml** と **udt**) を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="85615-109">These enhancements allow ADO applications to use newer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] features and to consume two data types introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]: **xml** and **udt**.</span></span> <span data-ttu-id="85615-110">また、この機能強化では、**varchar**、**nvarchar**、**varbinary** の各データ型に対する機能も強化されています。</span><span class="sxs-lookup"><span data-stu-id="85615-110">These enhancements also exploit enhancements to the **varchar**, **nvarchar**, and **varbinary** data types.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="85615-111">Native Client では、ado アプリケーションで使用するために、SSPROP_INIT_DATATYPECOMPATIBILITY 初期化プロパティが DBPROPSET_SQLSERVERDBINIT プロパティセットに追加されます。これにより、新しいデータ型が ADO と互換性のある方法で公開されるようになります。</span><span class="sxs-lookup"><span data-stu-id="85615-111">Native Client adds the SSPROP_INIT_DATATYPECOMPATIBILITY initialization property to the DBPROPSET_SQLSERVERDBINIT property set for use by ADO applications so that the new data types are exposed in a way compatible with ADO.</span></span> <span data-ttu-id="85615-112">また、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、 `DataTypeCompatibility` 接続文字列で設定されるという名前の新しい接続文字列キーワードも定義します。</span><span class="sxs-lookup"><span data-stu-id="85615-112">In addition, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider also defines a new connection string keyword named `DataTypeCompatibility` that is set in the connection string.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="85615-113">既存の ADO アプリケーションは、SQLOLEDB プロバイダーを使用して、XML、UDT、および大きな値のテキストやバイナリのフィールド値にアクセスして更新できます。</span><span class="sxs-lookup"><span data-stu-id="85615-113">Existing ADO applications can access and update XML, UDT, and large value text and binary field values using the SQLOLEDB provider.</span></span> <span data-ttu-id="85615-114">サイズの大きな値をとる新しいデータ型 **varchar(max)** 、**nvarchar(max)** 、**varbinary(max)** はそれぞれ、**adLongVarChar**、**adLongVarWChar**、**adLongVarBinary** という ADO 型として返されます。</span><span class="sxs-lookup"><span data-stu-id="85615-114">The new larger **varchar(max)**, **nvarchar(max)**, and **varbinary(max)** data types are returned as the ADO types **adLongVarChar**, **adLongVarWChar** and **adLongVarBinary** respectively.</span></span> <span data-ttu-id="85615-115">XML 列は **adLongVarChar** として返され、UDT 列は **adVarBinary** として返されます。</span><span class="sxs-lookup"><span data-stu-id="85615-115">XML columns are returned as **adLongVarChar**, and UDT columns are returned as **adVarBinary**.</span></span> <span data-ttu-id="85615-116">ただし、SQLOLEDB ではなく [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダー (SQLNCLI11) を使用する場合は、新しいデータ型が ADO データ型に正しく対応するように、`DataTypeCompatibility` キーワードを "80" に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85615-116">However, if you use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider (SQLNCLI11) instead of SQLOLEDB, you need to make sure to set the `DataTypeCompatibility` keyword to "80" so that the new data types will map correctly to the ADO data types.</span></span>  
  
## <a name="enabling-sql-server-native-client-from-ado"></a><span data-ttu-id="85615-117">ADO からの SQL Server Native Client の有効化</span><span class="sxs-lookup"><span data-stu-id="85615-117">Enabling SQL Server Native Client from ADO</span></span>  
 <span data-ttu-id="85615-118">Native Client の使用を有効にするに [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、ADO アプリケーションで、接続文字列に次のキーワードを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85615-118">To enable the usage of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, ADO applications will need to implement the following keywords in their connection strings:</span></span>  
  
-   `Provider=SQLNCLI11`  
  
-   `DataTypeCompatibility=80`  
  
 <span data-ttu-id="85615-119">Native Client でサポートされている ADO 接続文字列キーワードの詳細については [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、「 [SQL Server Native Client での接続文字列キーワードの使用](using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85615-119">For more information about the ADO connections string keywords supported in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Using Connection String Keywords with SQL Server Native Client](using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="85615-120">次の例では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] MARS 機能の有効化など、Native Client で動作するように完全に有効になっている ADO 接続文字列を確立しています。</span><span class="sxs-lookup"><span data-stu-id="85615-120">The following is an example of establishing an ADO connection string that is fully enabled to work with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, including the enabling of the MARS feature:</span></span>  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  
  
## <a name="examples"></a><span data-ttu-id="85615-121">例</span><span class="sxs-lookup"><span data-stu-id="85615-121">Examples</span></span>  
 <span data-ttu-id="85615-122">次のセクションでは、Native Client OLE DB プロバイダーで ADO を使用する方法の例について説明し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="85615-122">The following sections provide examples of how you can use ADO with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
### <a name="retrieving-xml-column-data"></a><span data-ttu-id="85615-123">XML 列データの取得</span><span class="sxs-lookup"><span data-stu-id="85615-123">Retrieving XML Column Data</span></span>  
 <span data-ttu-id="85615-124">この例では、レコードセットを使用し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** サンプル データベースの XML 列からデータを取得および表示します。</span><span class="sxs-lookup"><span data-stu-id="85615-124">In this example, a recordset is used to retrieve and display the data from an XML column in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **AdventureWorks** sample database.</span></span>  
  
```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  
  
' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  
  
con.Close  
Set con = Nothing  
```  
  
> [!NOTE]  
>  <span data-ttu-id="85615-125">レコードセットのフィルター選択は、XML 列でサポートされません。</span><span class="sxs-lookup"><span data-stu-id="85615-125">Recordset filtering is not supported with XML columns.</span></span> <span data-ttu-id="85615-126">これを使用すると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="85615-126">If used, an error will be returned.</span></span>  
  
### <a name="retrieving-udt-column-data"></a><span data-ttu-id="85615-127">UDT 列データの取得</span><span class="sxs-lookup"><span data-stu-id="85615-127">Retrieving UDT Column Data</span></span>  
 <span data-ttu-id="85615-128">この例では、**Command** オブジェクトを使用して、UDT を返す SQL クエリを実行します。その後、UDT データを更新し、新しいデータをデータベースに挿入します。</span><span class="sxs-lookup"><span data-stu-id="85615-128">In this example, a **Command** object is used to execute a SQL query that returns a UDT, the UDT data is updated, and then the new data is inserted back into the database.</span></span> <span data-ttu-id="85615-129">ここでは、**Point** UDT が既にデータベースに登録されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="85615-129">This example assumes that the **Point** UDT has already been registered in the database.</span></span>  
  
```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  
  
con.Open  
  
' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  
  
' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  
  
' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  
  
con.Close  
Set con = Nothing  
```  
  
### <a name="enabling-and-using-mars"></a><span data-ttu-id="85615-130">MARS の有効化と使用</span><span class="sxs-lookup"><span data-stu-id="85615-130">Enabling and Using MARS</span></span>  
 <span data-ttu-id="85615-131">この例では、Native Client OLE DB プロバイダーを介して MARS を有効にするように接続文字列が構築され、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 同じ接続を使用して実行するために2つのレコードセットオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="85615-131">In this example, the connection string is constructed to enable MARS through the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, and then two recordset objects are created to execute using the same connection.</span></span>  
  
```  
Dim con As New ADODB.Connection  
  
con.ConnectionString = "Provider=SQLNCLI11;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
  
Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  
  
Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  
  
con.Close  
Set con = Nothing  
```  
  
 <span data-ttu-id="85615-132">以前のバージョンの OLE DB プロバイダーでは、アクティブな結果セットを 1 つの接続ごとに 1 つしか開くことができなかったので、このコードにより 2 回目の実行時に暗黙の接続が作成されました。</span><span class="sxs-lookup"><span data-stu-id="85615-132">In prior versions of the OLE DB provider, this code would cause an implicit connection to be created on the second execution because only one active set of results could be opened per a single connection.</span></span> <span data-ttu-id="85615-133">暗黙の接続が OLE DB 接続プールにプールされなかったので、これが原因でオーバーヘッドが増加することになります。</span><span class="sxs-lookup"><span data-stu-id="85615-133">Because the implicit connection was not pooled in the OLE DB connection pool this would cause additional overhead.</span></span> <span data-ttu-id="85615-134">Native Client OLE DB プロバイダーによって公開されている MARS 機能を使用すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 1 つの接続で複数のアクティブな結果を取得できます。</span><span class="sxs-lookup"><span data-stu-id="85615-134">With the MARS feature exposed by the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you get multiple active results on the one connection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85615-135">参照</span><span class="sxs-lookup"><span data-stu-id="85615-135">See Also</span></span>  
 [<span data-ttu-id="85615-136">SQL Server Native Client を使用したアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="85615-136">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
