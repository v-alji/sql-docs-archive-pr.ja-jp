---
title: OLE DB ソース | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbsource.f1
helpviewer_keywords:
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: f87cc5f6-b078-40f3-9d87-7a65e13e4c86
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce0d2a95639dc31ee8cf4dd9cdaca6844ad4a1d9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633936"
---
# <a name="ole-db-source"></a><span data-ttu-id="e86d1-102">OLE DB ソース</span><span class="sxs-lookup"><span data-stu-id="e86d1-102">OLE DB Source</span></span>
  <span data-ttu-id="e86d1-103">OLE DB ソースは、データベース テーブル、ビュー、または SQL コマンドを使用して、OLE DB に準拠するさまざまなリレーショナル データベースからデータを抽出します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-103">The OLE DB source extracts data from a variety of OLE DB-compliant relational databases by using a database table, a view, or an SQL command.</span></span> <span data-ttu-id="e86d1-104">たとえば、OLE DB ソースにより、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのテーブルからデータを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-104">For example, the OLE DB source can extract data from tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="e86d1-105">OLE DB ソースには、データを抽出するために、次の 4 つの異なるデータ アクセス モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e86d1-105">The OLE DB source provides four different data access modes for extracting data:</span></span>  
  
-   <span data-ttu-id="e86d1-106">テーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="e86d1-106">A table or view.</span></span>  
  
-   <span data-ttu-id="e86d1-107">変数で指定されたテーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="e86d1-107">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="e86d1-108">SQL ステートメントの結果。</span><span class="sxs-lookup"><span data-stu-id="e86d1-108">The results of an SQL statement.</span></span> <span data-ttu-id="e86d1-109">クエリにはパラメーター化クエリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-109">The query can be a parameterized query.</span></span>  
  
-   <span data-ttu-id="e86d1-110">変数に格納された SQL ステートメントの結果。</span><span class="sxs-lookup"><span data-stu-id="e86d1-110">The results of an SQL statement stored in a variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e86d1-111">SQL ステートメントを使用して、一時テーブルから結果を返すストアド プロシージャが呼び出す場合は、WITH RESULT SETS オプションを使用して結果セットのメタデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-111">When you use an SQL statement to invoke a stored procedure that returns results from a temporary table, use the WITH RESULT SETS option to define metadata for the result set.</span></span>  
  
 <span data-ttu-id="e86d1-112">パラメーター化クエリを使用すると、変数をパラメーターにマップして、SQL ステートメント内の個別のパラメーターの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-112">If you use a parameterized query, you can map variables to parameters to specify the values for individual parameters in the SQL statements.</span></span>  
  
 <span data-ttu-id="e86d1-113">OLE DB ソースは、OLE DB 接続マネージャーを使用してデータ ソースに接続します。OLE DB 接続マネージャーは、使用する OLE DB プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-113">This source uses an OLE DB connection manager to connect to a data source, and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="e86d1-114">詳細については、「 [OLE DB 接続マネージャー](../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e86d1-114">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="e86d1-115">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトでは、OLE DB 接続マネージャーを作成できるデータ ソース オブジェクトも用意されています。このオブジェクトは、データ ソースとデータ ソース ビューを OLE DB ソースで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e86d1-115">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, making data sources and data source views available to the OLE DB source.</span></span>  
  
 <span data-ttu-id="e86d1-116">OLE DB プロバイダーによっては、OLE DB ソースに次のような制限が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e86d1-116">Depending on the OLE DB provider, some limitations apply to the OLE DB source:</span></span>  
  
-   <span data-ttu-id="e86d1-117">Oracle 用の [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB プロバイダーは、Oracle データ型の BLOB、CLOB、NCLOB、BFILE、および UROWID 型をサポートしていないため、OLE DB ソースは、これらのデータ型の列が含まれるテーブルからデータを抽出できません。</span><span class="sxs-lookup"><span data-stu-id="e86d1-117">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB provider for Oracle does not support the Oracle data types BLOB, CLOB, NCLOB, BFILE, OR UROWID, and the OLE DB source cannot extract data from tables that contain columns with these data types.</span></span>  
  
-   <span data-ttu-id="e86d1-118">IBM OLE DB DB2 プロバイダーおよび [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 プロバイダーは、ストアド プロシージャを呼び出す SQL コマンドの使用をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e86d1-118">The IBM OLE DB DB2 provider and [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB DB2 provider do not support using an SQL command that calls a stored procedure.</span></span> <span data-ttu-id="e86d1-119">この種類のコマンドを使用すると、OLE DB ソースは列のメタデータを作成できません。その結果、データ フロー内で OLE DB ソースの後に実行されるデータ フロー コンポーネントでは、使用できる列データがないため、データ フローの実行が失敗します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-119">When this kind of command is used, the OLE DB source cannot create the column metadata and, as a result, the data flow components that follow the OLE DB source in the data flow have no column data available and the execution of the data flow fails.</span></span>  
  
 <span data-ttu-id="e86d1-120">OLE DB ソースは、1 つの標準出力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="e86d1-120">The OLE DB source has one regular output and one error output.</span></span>  
  
## <a name="using-parameterized-sql-statements"></a><span data-ttu-id="e86d1-121">パラメーター化された SQL ステートメントの使用</span><span class="sxs-lookup"><span data-stu-id="e86d1-121">Using Parameterized SQL Statements</span></span>  
 <span data-ttu-id="e86d1-122">OLE DB ソースは、SQL ステートメントを使用してデータを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-122">The OLE DB source can use an SQL statement to extract data.</span></span> <span data-ttu-id="e86d1-123">使用できるのは、SELECT ステートメントまたは EXEC ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="e86d1-123">The statement can be a SELECT or an EXEC statement.</span></span>  
  
 <span data-ttu-id="e86d1-124">OLE DB ソースは、OLE DB 接続マネージャーを使用して、データの抽出元からデータ ソースに接続します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-124">The OLE DB source uses an OLE DB connection manager to connect to the data source from which it extracts data.</span></span> <span data-ttu-id="e86d1-125">OLE DB 接続マネージャーが使用するプロバイダー、および接続マネージャーの接続先であるリレーショナル データベース管理システム (RDBMS) によって、異なる規則がパラメーターの名前付けや一覧表示に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-125">Depending on the provider that the OLE DB connection manager uses and the Relational Database Management System (RDBMS) that the connection manager connects to, different rules apply to the naming and listing of parameters.</span></span> <span data-ttu-id="e86d1-126">パラメーター名が RDBMS から返される場合、パラメーター名を使用して、パラメーター リストのパラメーターを SQL ステートメントのパラメーターにマップできます。それ以外の場合は、パラメーターがパラメーター リストの序数位置によって SQL ステートメントのパラメーターにマップされます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-126">If the parameter names are returned from the RDBMS, you can use parameter names to map parameters in a parameter list to parameters in an SQL statement; otherwise, the parameters are mapped to the parameter in the SQL statement by their ordinal position in the parameter list.</span></span> <span data-ttu-id="e86d1-127">サポートされるパラメーター名の種類は、プロバイダーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="e86d1-127">The types of parameter names that are supported vary by provider.</span></span> <span data-ttu-id="e86d1-128">たとえば、変数名または列名の使用を必要とするプロバイダーや、0 や Param0 などのシンボルの名前の使用を必要とするプロバイダーがあります。</span><span class="sxs-lookup"><span data-stu-id="e86d1-128">For example, some providers require that you use the variable or column names, whereas some providers require that you use symbolic names such as 0 or Param0.</span></span> <span data-ttu-id="e86d1-129">SQL ステートメントで使用するパラメーター名の詳細については、プロバイダー固有のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e86d1-129">You should see the provider-specific documentation for information about the parameter names to use in SQL statements.</span></span>  
  
 <span data-ttu-id="e86d1-130">OLE DB 接続マネージャーを使用する場合、パラメーター化サブクエリは使用できません。これは、OLE DB ソースが OLE DB プロバイダーを介してパラメーター情報を取得できないからです。</span><span class="sxs-lookup"><span data-stu-id="e86d1-130">When you are use an OLE DB connection manager, you cannot use parameterized subqueries, because the OLE DB source cannot derive parameter information through the OLE DB provider.</span></span> <span data-ttu-id="e86d1-131">ただし、式を使用することで、パラメーター値をクエリ文字列に連結したり、ソースの SqlCommand プロパティを設定したりできます。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーでは、 **[OLE DB ソース エディター]** ダイアログ ボックスを使用して OLE DB ソースを構成し、 **[クエリ パラメーターの設定]** ダイアログ ボックスで変数にパラメーターをマップします。</span><span class="sxs-lookup"><span data-stu-id="e86d1-131">However, you can use an expression to concatenate the parameter values into the query string and to set the SqlCommand property of the source.In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, you configure an OLE DB source by using the **OLE DB Source Editor** dialog box and map the parameters to variables in the **Set Query Parameter** dialog box.</span></span>  
  
### <a name="specifying-parameters-by-using-ordinal-positions"></a><span data-ttu-id="e86d1-132">序数位置を使用したパラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="e86d1-132">Specifying Parameters by Using Ordinal Positions</span></span>  
 <span data-ttu-id="e86d1-133">パラメーター名が返されない場合は、 **[クエリ パラメーターの設定]** ダイアログ ボックスの **[パラメーター]** ボックスの一覧にパラメーターが表示されている順序で、実行時にパラメーターがどのパラメーター マーカーにマップされるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="e86d1-133">If no parameter names are returned, the order in which the parameters are listed in the **Parameters** list in the **Set Query Parameter** dialog box governs which parameter marker they are mapped to at run time.</span></span> <span data-ttu-id="e86d1-134">一覧に表示されている最初のパラメーターは SQL ステートメントの最初の ? にマップされ、</span><span class="sxs-lookup"><span data-stu-id="e86d1-134">The first parameter in the list maps to the first ?</span></span> <span data-ttu-id="e86d1-135">2 番目のパラメーターは 2 番目の ? にマップされ、それ以降同様にマップされます</span><span class="sxs-lookup"><span data-stu-id="e86d1-135">in the SQL statement, the second to the second ?, and so on.</span></span>  
  
 <span data-ttu-id="e86d1-136">次の SQL ステートメントは、 **データベースの** Product [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] テーブルから行を選択します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-136">The following SQL statement selects rows from the **Product** table in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span> <span data-ttu-id="e86d1-137">**[マッピング]** ボックスの一覧に表示される最初のパラメーターは **Color** 列の最初のパラメーターに、2 番目のパラメーターは **Size** 列にマップされます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-137">The first parameter in the **Mappings** list maps to the first parameter to the **Color** column, the second parameter to the **Size** column.</span></span>  
  
 `SELECT * FROM Production.Product WHERE Color = ? AND Size = ?`  
  
 <span data-ttu-id="e86d1-138">パラメーター名は順序に影響しません。</span><span class="sxs-lookup"><span data-stu-id="e86d1-138">The parameter names have no effect.</span></span> <span data-ttu-id="e86d1-139">たとえば、パラメーターの名前が適用先の列と同じ名前で、そのパラメーターが **[パラメーター]** ボックス内の正しい序数位置にない場合も、実行時に行われるパラメーター マッピングには、パラメーター名ではなく、パラメーターの序数位置が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-139">For example, if a parameter is named the same as the column to which it applies, but not put in the correct ordinal position in the **Parameters** list, the parameter mapping that occurs at run time will use the ordinal position of the parameter, not the parameter name.</span></span>  
  
 <span data-ttu-id="e86d1-140">通常、EXEC コマンドでは、プロシージャのパラメーター値を指定する変数の名前をパラメーター名として使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e86d1-140">The EXEC command typically requires that you use the names of the variables that provide parameter values in the procedure as parameter names.</span></span>  
  
### <a name="specifying-parameters-by-using-names"></a><span data-ttu-id="e86d1-141">名前を使用したパラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="e86d1-141">Specifying Parameters by Using Names</span></span>  
 <span data-ttu-id="e86d1-142">実際のパラメーター名が RDBMS から返される場合、SELECT ステートメントと EXEC ステートメントで使用されるパラメーターは名前によってマップされます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-142">If the actual parameter names are returned from the RDBMS, the parameters used by a SELECT and EXEC statement are mapped by name.</span></span> <span data-ttu-id="e86d1-143">このパラメーター名は、SELECT ステートメントまたは EXEC ステートメントによって実行されるストアド プロシージャで必要な名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e86d1-143">The parameter names must match the names that the stored procedure, run by the SELECT statement or the EXEC statement, expects.</span></span>  
  
 <span data-ttu-id="e86d1-144">次の SQL ステートメントは、 **データベースで利用できる** uspGetWhereUsedProductID [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] ストアド プロシージャを実行します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-144">The following SQL statement runs the **uspGetWhereUsedProductID** stored procedure, available in the [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)] database.</span></span>  
  
 `EXEC uspGetWhereUsedProductID ?, ?`  
  
 <span data-ttu-id="e86d1-145">このストアド プロシージャでは、パラメーター値を指定するために変数 `@StartProductID` と `@CheckDate`を必要としています。</span><span class="sxs-lookup"><span data-stu-id="e86d1-145">The stored procedure expects the variables, `@StartProductID` and `@CheckDate`, to provide parameter values.</span></span> <span data-ttu-id="e86d1-146">パラメーターが **[マッピング]** ボックスの一覧に表示される順序は関係ありません。</span><span class="sxs-lookup"><span data-stu-id="e86d1-146">The order in which the parameters appear in the **Mappings** list is irrelevant.</span></span> <span data-ttu-id="e86d1-147">ここで必要となるのは、パラメーター名が、\@ 記号を含めて、ストアド プロシージャの変数名と一致することのみです。</span><span class="sxs-lookup"><span data-stu-id="e86d1-147">The only requirement is that the parameter names match the variable names in the stored procedure, including the \@ sign.</span></span>  
  
### <a name="mapping-parameters-to-variables"></a><span data-ttu-id="e86d1-148">パラメーターの変数へのマッピング</span><span class="sxs-lookup"><span data-stu-id="e86d1-148">Mapping Parameters to Variables</span></span>  
 <span data-ttu-id="e86d1-149">パラメーターは、実行時にパラメーター値を提供する変数にマップされます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-149">The parameters are mapped to variables that provide the parameter values at run time.</span></span> <span data-ttu-id="e86d1-150">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に用意されているシステム変数を使用することもできますが、通常はユーザー定義変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-150">The variables are typically user-defined variables, although you can also use the system variables that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides.</span></span> <span data-ttu-id="e86d1-151">ユーザー定義変数を使用する場合、この変数に設定するデータ型は、パラメーター参照がマップされている列のデータ型との互換性があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e86d1-151">If you use user-defined variables, make sure that you set the data type to a type that is compatible with the data type of the column that the mapped parameter references.</span></span> <span data-ttu-id="e86d1-152">詳細については、「 [Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e86d1-152">For more information, see [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="troubleshooting-the-ole-db-source"></a><span data-ttu-id="e86d1-153">OLE DB ソースのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e86d1-153">Troubleshooting the OLE DB Source</span></span>  
 <span data-ttu-id="e86d1-154">OLE DB ソースによる外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-154">You can log the calls that the OLE DB source makes to external data providers.</span></span> <span data-ttu-id="e86d1-155">このログ機能を使用すると、OLE DB ソースによる外部データ ソースからのデータ読み込みに関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-155">You can use this logging capability to troubleshoot the loading of data from external data sources that the OLE DB source performs.</span></span> <span data-ttu-id="e86d1-156">OLE DB ソースによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="e86d1-156">To log the calls that the OLE DB source makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="e86d1-157">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e86d1-157">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-source"></a><span data-ttu-id="e86d1-158">OLE DB ソースの構成</span><span class="sxs-lookup"><span data-stu-id="e86d1-158">Configuring the OLE DB Source</span></span>  
 <span data-ttu-id="e86d1-159">プロパティはプログラムによって設定するか、または [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから設定できます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-159">You can set properties programmatically or through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="e86d1-160">**[OLE DB ソース エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e86d1-160">For more information about the properties that you can set in the **OLE DB Source Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="e86d1-161">[OLE DB ソース エディター &#40;[接続マネージャー] ページ&#41;](../ole-db-source-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="e86d1-161">[OLE DB Source Editor &#40;Connection Manager Page&#41;](../ole-db-source-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="e86d1-162">[OLE DB ソース エディター &#40;[列] ページ&#41;](../ole-db-source-editor-columns-page.md)</span><span class="sxs-lookup"><span data-stu-id="e86d1-162">[OLE DB Source Editor &#40;Columns Page&#41;](../ole-db-source-editor-columns-page.md)</span></span>  
  
-   <span data-ttu-id="e86d1-163">[OLE DB ソース エディター &#40;[エラー出力] ページ&#41;](../ole-db-source-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="e86d1-163">[OLE DB Source Editor &#40;Error Output Page&#41;](../ole-db-source-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="e86d1-164">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="e86d1-164">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="e86d1-165">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e86d1-165">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="e86d1-166">Common Properties</span><span class="sxs-lookup"><span data-stu-id="e86d1-166">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="e86d1-167">OLE DB カスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="e86d1-167">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
## <a name="related-tasks"></a><span data-ttu-id="e86d1-168">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="e86d1-168">Related Tasks</span></span>  
  
-   [<span data-ttu-id="e86d1-169">OLE DB 変換元を使用してデータを抽出する</span><span class="sxs-lookup"><span data-stu-id="e86d1-169">Extract Data by Using the OLE DB Source</span></span>](ole-db-source.md)  
  
-   [<span data-ttu-id="e86d1-170">クエリ パラメーターをデータ フロー コンポーネントの変数にマップする</span><span class="sxs-lookup"><span data-stu-id="e86d1-170">Map Query Parameters to Variables in a Data Flow Component</span></span>](map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
-   [<span data-ttu-id="e86d1-171">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="e86d1-171">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
-   [<span data-ttu-id="e86d1-172">マージ変換およびマージ結合変換用にデータを並べ替える</span><span class="sxs-lookup"><span data-stu-id="e86d1-172">Sort Data for the Merge and Merge Join Transformations</span></span>](transformations/sort-data-for-the-merge-and-merge-join-transformations.md)  
  
## <a name="related-content"></a><span data-ttu-id="e86d1-173">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="e86d1-173">Related Content</span></span>  
 <span data-ttu-id="e86d1-174">social.technet.microsoft.com の Wiki の記事「 [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670)(SSIS から Oracle への接続)」</span><span class="sxs-lookup"><span data-stu-id="e86d1-174">Wiki article, [SSIS with Oracle Connectors](https://go.microsoft.com/fwlink/?LinkId=220670), on social.technet.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e86d1-175">参照</span><span class="sxs-lookup"><span data-stu-id="e86d1-175">See Also</span></span>  
 <span data-ttu-id="e86d1-176">[OLE DB 変換先](ole-db-destination.md) </span><span class="sxs-lookup"><span data-stu-id="e86d1-176">[OLE DB Destination](ole-db-destination.md) </span></span>  
 <span data-ttu-id="e86d1-177">[Integration Services &#40;SSIS&#41; の変数](../integration-services-ssis-variables.md) </span><span class="sxs-lookup"><span data-stu-id="e86d1-177">[Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md) </span></span>  
 [<span data-ttu-id="e86d1-178">データ フロー</span><span class="sxs-lookup"><span data-stu-id="e86d1-178">Data Flow</span></span>](data-flow.md)  
  
  
