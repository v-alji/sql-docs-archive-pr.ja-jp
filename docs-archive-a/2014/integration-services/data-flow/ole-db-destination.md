---
title: OLE DB 変換先 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbdest.f1
helpviewer_keywords:
- fast-load data access mode [Integration Services]
- OLE DB destination [Integration Services]
- fast load options [Integration Services]
- fast-load options [Integration Services]
- destinations [Integration Services], OLE DB
- fast load data access mode [Integration Services]
- inserting data
ms.assetid: 873a2fa0-2a02-41fc-a80a-ec9767f36a8a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5227175e80db3a8f31a8b8db8c3d6bee3061bae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633938"
---
# <a name="ole-db-destination"></a><span data-ttu-id="67887-102">OLE DB 変換先</span><span class="sxs-lookup"><span data-stu-id="67887-102">OLE DB Destination</span></span>
  <span data-ttu-id="67887-103">OLE DB 変換先は、データベースのテーブルやビュー、または SQL コマンドを使用して、OLE DB に準拠するさまざまなデータベースにデータを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="67887-103">The OLE DB destination loads data into a variety of OLE DB-compliant databases using a database table or view or an SQL command.</span></span> <span data-ttu-id="67887-104">たとえば、OLE DB ソースにより、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータベースのテーブルにデータを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="67887-104">For example, the OLE DB source can load data into tables in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office Access and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="67887-105">OLE DB 変換先には、データを読み込むために、次の 5 つの異なるデータ アクセス モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="67887-105">The OLE DB destination provides five different data access modes for loading data:</span></span>  
  
-   <span data-ttu-id="67887-106">テーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="67887-106">A table or view.</span></span> <span data-ttu-id="67887-107">既存のテーブルまたはビューを指定できます。または、新しいテーブルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="67887-107">You can specify an existing table or view, or you create a new table.</span></span>  
  
-   <span data-ttu-id="67887-108">テーブルまたはビュー (高速読み込みオプションを使用)。</span><span class="sxs-lookup"><span data-stu-id="67887-108">A table or view using fast-load options.</span></span> <span data-ttu-id="67887-109">既存のテーブルを指定できます。または新しいテーブルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="67887-109">You can specify an existing table or create a new table.</span></span>  
  
-   <span data-ttu-id="67887-110">変数で指定されたテーブルまたはビュー。</span><span class="sxs-lookup"><span data-stu-id="67887-110">A table or view specified in a variable.</span></span>  
  
-   <span data-ttu-id="67887-111">変数で指定されたテーブルまたはビュー (高速読み込みオプションを使用)。</span><span class="sxs-lookup"><span data-stu-id="67887-111">A table or view specified in a variable using fast-load options.</span></span>  
  
-   <span data-ttu-id="67887-112">SQL ステートメントの結果。</span><span class="sxs-lookup"><span data-stu-id="67887-112">The results of an SQL statement.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67887-113">OLE DB 変換先ではパラメーターがサポートされません。</span><span class="sxs-lookup"><span data-stu-id="67887-113">The OLE DB destination does not support parameters.</span></span> <span data-ttu-id="67887-114">パラメーター化された INSERT ステートメントを実行する必要がある場合は、OLE DB コマンド変換を検討してください。</span><span class="sxs-lookup"><span data-stu-id="67887-114">If you need to execute a parameterized INSERT statement, consider the OLE DB Command transformation.</span></span> <span data-ttu-id="67887-115">詳細については、「 [OLE DB Command Transformation](transformations/ole-db-command-transformation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67887-115">For more information, see [OLE DB Command Transformation](transformations/ole-db-command-transformation.md).</span></span>  
  
 <span data-ttu-id="67887-116">OLE DB 変換先で 2 バイト文字セット (DBCS) を使用するデータを読み込む際に、データ アクセス モードで高速読み込みオプションを使用せず、OLE DB 接続マネージャーが [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB) を使用している場合、そのデータは破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="67887-116">When the OLE DB destination loads data that uses a double-byte character set (DBCS), the data may be corrupted if the data access mode does not use the fast load option and if the OLE DB connection manager uses the [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB Provider for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SQLOLEDB).</span></span> <span data-ttu-id="67887-117">DBCS データの整合性を保持するには、OLE DB 接続マネージャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用するように構成するか、次のどちらかの高速読み込みモードを使用する必要があります: **[テーブルまたはビュー - 高速読み込み]** または **[テーブル名またはビュー名の変数 - 高速読み込み]** 。</span><span class="sxs-lookup"><span data-stu-id="67887-117">To ensure the integrity of DBCS data you should configure the OLE DB connection manager to use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, or use one of the fast-load access modes: **Table or view - fast load** or **Table name or view name variable - fast load**.</span></span> <span data-ttu-id="67887-118">どちらのオプションも、 **[OLE DB 変換先エディター]** ダイアログ ボックスから使用できます。</span><span class="sxs-lookup"><span data-stu-id="67887-118">Both options are available from the **OLE DB Destination Editor** dialog box.</span></span> <span data-ttu-id="67887-119">オブジェクトモデルをプログラミングする場合は、 [!INCLUDE[ssIS](../../includes/ssis-md.md)] AccessMode プロパティをまたはに設定する必要があり `OpenRowset Using FastLoad` `OpenRowset Using FastLoad From Variable` ます。</span><span class="sxs-lookup"><span data-stu-id="67887-119">When programming the [!INCLUDE[ssIS](../../includes/ssis-md.md)] object model, you should set the AccessMode property to `OpenRowset Using FastLoad`, or `OpenRowset Using FastLoad From Variable`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67887-120">**デザイナーの** [OLE DB 変換先エディター] [!INCLUDE[ssIS](../../includes/ssis-md.md)] ダイアログ ボックスを使用して、OLE DB 変換先がデータを挿入する変換先テーブルを作成する際に、新しく作成したテーブルを手動で選択する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="67887-120">If you use the **OLE DB Destination Editor** dialog box in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer to create the destination table into which the OLE DB destination inserts data, you may have to select the newly created table manually.</span></span> <span data-ttu-id="67887-121">手動で選択する必要があるのは、OLE DB provider for DB2 などの OLE DB プロバイダーが、スキーマの識別子を自動的にテーブル名に追加した場合です。</span><span class="sxs-lookup"><span data-stu-id="67887-121">The need for manual selection occurs when an OLE DB provider, such as the OLE DB provider for DB2, automatically adds schema identifiers to the table name.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67887-122">変換先の種類に応じて、 **[OLE DB 変換先エディター]** ダイアログ ボックスによって生成される CREATE TABLE ステートメントの変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="67887-122">The CREATE TABLE statement that the **OLE DB Destination Editor** dialog box generates may require modification depending on the destination type.</span></span> <span data-ttu-id="67887-123">たとえば、変換先によっては CREATE TABLE ステートメントで使用されるデータ型をサポートしない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="67887-123">For example, some destinations do not support the data types that the CREATE TABLE statement uses.</span></span>  
  
 <span data-ttu-id="67887-124">OLE DB 変換先は、OLE DB 接続マネージャーを使用してデータ ソースに接続します。OLE DB 接続マネージャーでは、使用する OLE DB プロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="67887-124">This destination uses an OLE DB connection manager to connect to a data source and the connection manager specifies the OLE DB provider to use.</span></span> <span data-ttu-id="67887-125">詳細については、「 [OLE DB 接続マネージャー](../connection-manager/ole-db-connection-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67887-125">For more information, see [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="67887-126">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトでは、OLE DB 接続マネージャーを作成できるデータ ソース オブジェクトも用意されています。このオブジェクトは、データ ソースとデータ ソース ビューを OLE DB 変換先で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="67887-126">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project also provides the data source object from which you can create an OLE DB connection manager, to make data sources and data source views available to the OLE DB destination.</span></span>  
  
 <span data-ttu-id="67887-127">OLE DB 変換先には、入力列と変換先データ ソースの列との間のマッピングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="67887-127">An OLE DB destination includes mappings between input columns and columns in the destination data source.</span></span> <span data-ttu-id="67887-128">入力列をすべての変換先列にマップする必要はありませんが、変換先列のプロパティによっては、変換先列にマップされる入力列がない場合、エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="67887-128">You do not have to map input columns to all destination columns, but depending on the properties of the destination columns, errors can occur if no input columns are mapped to the destination columns.</span></span> <span data-ttu-id="67887-129">たとえば、入力先列で NULL 値が許容されていない場合は、入力列をその列にマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="67887-129">For example, if a destination column does not allow null values, an input column must be mapped to that column.</span></span> <span data-ttu-id="67887-130">また、マップされる列のデータ型には互換性がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="67887-130">In addition, the data types of mapped columns must be compatible.</span></span> <span data-ttu-id="67887-131">たとえば、文字列データ型の入力列を数値データ型の変換先列にマップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="67887-131">For example, you cannot map an input column with a string data type to a destination column with a numeric data type.</span></span>  
  
 <span data-ttu-id="67887-132">OLE DB 変換先は、1 つの標準入力と 1 つのエラー出力をとります。</span><span class="sxs-lookup"><span data-stu-id="67887-132">The OLE DB destination has one regular input and one error output.</span></span>  
  
 <span data-ttu-id="67887-133">データ型について詳しくは、「 [Integration Services のデータ型](integration-services-data-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="67887-133">For more information about data types, see [Integration Services Data Types](integration-services-data-types.md).</span></span>  
  
## <a name="fast-load-options"></a><span data-ttu-id="67887-134">高速読み込みオプション</span><span class="sxs-lookup"><span data-stu-id="67887-134">Fast Load Options</span></span>  
 <span data-ttu-id="67887-135">OLE DB 変換先で高速読み込みデータ アクセス モードが使用される場合、 **[OLE DB 変換先エディター]** のユーザー インターフェイスで、変換先に対して次の高速読み込みオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="67887-135">If the OLE DB destination uses a fast-load data access mode, you can specify the following fast load options in the user interface, **OLE DB Destination Editor**, for the destination:</span></span>  
  
-   <span data-ttu-id="67887-136">インポートしたデータ ファイルの ID 値を保持します。または、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によって割り当てられた一意の値を使用します。</span><span class="sxs-lookup"><span data-stu-id="67887-136">Keep identity values from the imported data file or use unique values assigned by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="67887-137">一括読み込み操作中に、NULL 値を保持します。</span><span class="sxs-lookup"><span data-stu-id="67887-137">Retain a null value during the bulk load operation.</span></span>  
  
-   <span data-ttu-id="67887-138">一括インポート操作中に、インポート先のテーブルまたはビューに対して CHECK 制約を実行します。</span><span class="sxs-lookup"><span data-stu-id="67887-138">Check constraints on the target table or view during the bulk import operation.</span></span>  
  
-   <span data-ttu-id="67887-139">一括読み込み操作中に、テーブルレベルのロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="67887-139">Acquire a table-level lock for the duration of the bulk load operation.</span></span>  
  
-   <span data-ttu-id="67887-140">バッチの行数およびコミット サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="67887-140">Specify the number of rows in the batch and the commit size.</span></span>  
  
 <span data-ttu-id="67887-141">一部の高速読み込みオプションは、OLE DB 変換先の特定のプロパティに格納されています。</span><span class="sxs-lookup"><span data-stu-id="67887-141">Some fast load options are stored in specific properties of the OLE DB destination.</span></span> <span data-ttu-id="67887-142">たとえば、ID 値を保持するかどうかを指定する FastLoadKeepIdentity、NULL 値を保持するかどうかを指定する FastLoadKeepNulls、バッチとしてコミットする行数を指定する FastLoadMaxInsertCommitSize などがあります。</span><span class="sxs-lookup"><span data-stu-id="67887-142">For example, FastLoadKeepIdentity specifies whether to keep identify values, FastLoadKeepNulls specifies whether to keep null values, and FastLoadMaxInsertCommitSize specifies the number of rows to commit as a batch.</span></span> <span data-ttu-id="67887-143">その他の高速読み込みオプションは、FastLoadOptions プロパティのコンマ区切りリストで格納されます。</span><span class="sxs-lookup"><span data-stu-id="67887-143">Other fast load options are stored in a comma-separated list in the FastLoadOptions property.</span></span> <span data-ttu-id="67887-144">OLE DB 変換先が FastLoadOptions に格納されている高速読み込みオプションをすべて使用し、[ **OLE DB 変換先エディター** ] ダイアログボックスに一覧表示されている場合は、プロパティの値がに設定され `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000` ます。</span><span class="sxs-lookup"><span data-stu-id="67887-144">If the OLE DB destination uses all the fast load options that are stored in FastLoadOptions and listed in the **OLE DB Destination Editor** dialog box, the value of the property is set to `TABLOCK, CHECK_CONSTRAINTS, ROWS_PER_BATCH=1000`.</span></span> <span data-ttu-id="67887-145">値 1000 を設定すると、1,000 行のバッチを使用するように変換先が構成されます。</span><span class="sxs-lookup"><span data-stu-id="67887-145">The value 1000 indicates that the destination is configured to use batches of 1000 rows.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67887-146">変換先で制約が失敗すると、FastLoadMaxInsertCommitSize で定義された行数のバッチ全体が失敗します。</span><span class="sxs-lookup"><span data-stu-id="67887-146">Any constraint failure at the destination causes the entire batch of rows defined by FastLoadMaxInsertCommitSize to fail.</span></span>  
  
 <span data-ttu-id="67887-147">**[OLE DB 変換先エディター]** ダイアログ ボックスで公開される高速読み込みオプションに加えて、 **[詳細エディター]** ダイアログ ボックスで、FastLoadOptions プロパティに次の一括読み込みオプションを入力することにより、それらのオプションを使用するように OLE DB 変換先を構成できます。</span><span class="sxs-lookup"><span data-stu-id="67887-147">In addition to the fast load options exposed in the **OLE DB Destination Editor** dialog box,you can configure the OLE DB destination to use the following bulk load options by typing the options in FastLoadOptions property in the **Advanced Editor** dialog box.</span></span>  
  
|<span data-ttu-id="67887-148">高速読み込みオプション</span><span class="sxs-lookup"><span data-stu-id="67887-148">Fast load option</span></span>|<span data-ttu-id="67887-149">説明</span><span class="sxs-lookup"><span data-stu-id="67887-149">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="67887-150">KILOBYTES_PER_BATCH</span><span class="sxs-lookup"><span data-stu-id="67887-150">KILOBYTES_PER_BATCH</span></span>|<span data-ttu-id="67887-151">挿入するサイズを KB 単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="67887-151">Specifies the size in kilobytes to insert.</span></span> <span data-ttu-id="67887-152">このオプションの形式は `KILOBYTES_PER_BATCH`  =  \<positive integer value**> \* \* です。</span><span class="sxs-lookup"><span data-stu-id="67887-152">The option has the form `KILOBYTES_PER_BATCH` = \<positive integer value**>\*\*.</span></span>|  
|<span data-ttu-id="67887-153">FIRE_TRIGGERS</span><span class="sxs-lookup"><span data-stu-id="67887-153">FIRE_TRIGGERS</span></span>|<span data-ttu-id="67887-154">挿入テーブルでトリガーを起動するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="67887-154">Specifies whether triggers fire on the insert table.</span></span> <span data-ttu-id="67887-155">このオプションの形式は、 **FIRE_TRIGGERS**です。</span><span class="sxs-lookup"><span data-stu-id="67887-155">The option has the form **FIRE_TRIGGERS**.</span></span> <span data-ttu-id="67887-156">このオプションが指定されている場合は、トリガーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="67887-156">The presence of the option indicates that triggers fire.</span></span>|  
|<span data-ttu-id="67887-157">ORDER</span><span class="sxs-lookup"><span data-stu-id="67887-157">ORDER</span></span>|<span data-ttu-id="67887-158">入力データの並べ替え方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="67887-158">Specifies how the input data is sorted.</span></span> <span data-ttu-id="67887-159">このオプションの形式は、ORDER \<column name> ASC&#124;DESC です。</span><span class="sxs-lookup"><span data-stu-id="67887-159">The option has the form ORDER \<column name> ASC&#124;DESC.</span></span> <span data-ttu-id="67887-160">並べ替える列のリストには任意の数列を指定できます。並べ替え順序の指定は省略することもできます。</span><span class="sxs-lookup"><span data-stu-id="67887-160">Any number of columns may be listed and it is optional to include the sort order.</span></span> <span data-ttu-id="67887-161">並べ替え順序を指定しなかった場合は、データを並べ替えないと見なして挿入操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="67887-161">If sort order is omitted, the insert operation assumes the data is unsorted.</span></span><br /><br /> <span data-ttu-id="67887-162">注:ORDER オプションを使用してテーブル上のクラスター化インデックスに従って入力データを並べ替えると、パフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="67887-162">Note: Performance can be improved if you use the ORDER option to sort the input data according to the clustered index on the table.</span></span>|  
  
 <span data-ttu-id="67887-163">[!INCLUDE[tsql](../../includes/tsql-md.md)] キーワードは慣例として通常は大文字で入力しますが、これらのキーワードの大文字小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="67887-163">The [!INCLUDE[tsql](../../includes/tsql-md.md)] keywords are traditionally typed using uppercase letters, but the keywords are not case sensitive.</span></span>  
  
 <span data-ttu-id="67887-164">高速読み込みオプションの詳細については、「[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67887-164">To learn more about fast load options, see [BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql).</span></span>  
  
## <a name="troubleshooting-the-ole-db-destination"></a><span data-ttu-id="67887-165">OLE DB 変換先のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="67887-165">Troubleshooting the OLE DB Destination</span></span>  
 <span data-ttu-id="67887-166">OLE DB 変換先による外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="67887-166">You can log the calls that the OLE DB destination makes to external data providers.</span></span> <span data-ttu-id="67887-167">このログ機能を使用すると、OLE DB 変換先による外部データ ソースへのデータ保存に関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="67887-167">You can use this logging capability to troubleshoot the saving of data to external data sources that the OLE DB destination performs.</span></span> <span data-ttu-id="67887-168">OLE DB 変換先による外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択します。</span><span class="sxs-lookup"><span data-stu-id="67887-168">To log the calls that the OLE DB destination makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="67887-169">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67887-169">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
## <a name="configuring-the-ole-db-destination"></a><span data-ttu-id="67887-170">OLE DB 変換先の構成</span><span class="sxs-lookup"><span data-stu-id="67887-170">Configuring the OLE DB Destination</span></span>  
 <span data-ttu-id="67887-171">プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="67887-171">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="67887-172">**[OLE DB 変換先エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="67887-172">For more information about the properties that you can set in the **OLE DB Destination Editor** dialog box, click one of the following topics:</span></span>  
  
-   <span data-ttu-id="67887-173">[[OLE DB 変換先エディター] &#40;[接続マネージャー] ページ&#41;](../ole-db-destination-editor-connection-manager-page.md)</span><span class="sxs-lookup"><span data-stu-id="67887-173">[OLE DB Destination Editor &#40;Connection Manager Page&#41;](../ole-db-destination-editor-connection-manager-page.md)</span></span>  
  
-   <span data-ttu-id="67887-174">[[OLE DB 変換先エディター] &#40;[マッピング] ページ&#41;](../ole-db-destination-editor-mappings-page.md)</span><span class="sxs-lookup"><span data-stu-id="67887-174">[OLE DB Destination Editor &#40;Mappings Page&#41;](../ole-db-destination-editor-mappings-page.md)</span></span>  
  
-   <span data-ttu-id="67887-175">[[OLE DB 変換先エディター] &#40;[エラー出力] ページ&#41;](../ole-db-destination-editor-error-output-page.md)</span><span class="sxs-lookup"><span data-stu-id="67887-175">[OLE DB Destination Editor &#40;Error Output Page&#41;](../ole-db-destination-editor-error-output-page.md)</span></span>  
  
 <span data-ttu-id="67887-176">**[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。</span><span class="sxs-lookup"><span data-stu-id="67887-176">The **Advanced Editor** dialog box reflects the properties that can be set programmatically.</span></span> <span data-ttu-id="67887-177">**[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="67887-177">For more information about the properties that you can set in the **Advanced Editor** dialog box or programmatically, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="67887-178">Common Properties</span><span class="sxs-lookup"><span data-stu-id="67887-178">Common Properties</span></span>](../common-properties.md)  
  
-   [<span data-ttu-id="67887-179">OLE DB カスタム プロパティ</span><span class="sxs-lookup"><span data-stu-id="67887-179">OLE DB Custom Properties</span></span>](ole-db-custom-properties.md)  
  
 <span data-ttu-id="67887-180">プロパティの設定方法の詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="67887-180">For more information about how to set properties, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="67887-181">OLE DB 変換先を使用してデータを読み込む</span><span class="sxs-lookup"><span data-stu-id="67887-181">Load Data by Using the OLE DB Destination</span></span>](ole-db-destination.md)  
  
-   [<span data-ttu-id="67887-182">データ フロー コンポーネントのプロパティを設定する</span><span class="sxs-lookup"><span data-stu-id="67887-182">Set the Properties of a Data Flow Component</span></span>](set-the-properties-of-a-data-flow-component.md)  
  
## <a name="related-content"></a><span data-ttu-id="67887-183">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="67887-183">Related Content</span></span>  
 [<span data-ttu-id="67887-184">OLE DB 変換元</span><span class="sxs-lookup"><span data-stu-id="67887-184">OLE DB Source</span></span>](ole-db-source.md)  
  
 [<span data-ttu-id="67887-185">Integration Services &#40;SSIS&#41; の変数</span><span class="sxs-lookup"><span data-stu-id="67887-185">Integration Services &#40;SSIS&#41; Variables</span></span>](../integration-services-ssis-variables.md)  
  
 [<span data-ttu-id="67887-186">データ フロー</span><span class="sxs-lookup"><span data-stu-id="67887-186">Data Flow</span></span>](data-flow.md)  
  
  
