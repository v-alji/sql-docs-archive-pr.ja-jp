---
title: 一括読み込みのセキュリティに関する考慮事項 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, XML Bulk Load
- bulk load [SQLXML], security
- security [SQLXML], XML Bulk Load
- XML Bulk Load [SQLXML], security
ms.assetid: 192fc6d4-ecbc-4a4d-a5cb-55e1f64af318
author: rothja
ms.author: jroth
ms.openlocfilehash: 21c1cbe7f94ef42327aa7b81f75fa521d9f7c0e9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646132"
---
# <a name="bulk-load-security-considerations-sqlxml-40"></a><span data-ttu-id="966ad-102">一括読み込みのセキュリティに関する注意点 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="966ad-102">Bulk Load Security Considerations (SQLXML 4.0)</span></span>
  <span data-ttu-id="966ad-103">次に、XML 一括読み込みを使用する場合のセキュリティに関するガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="966ad-103">The following are security guidelines for using XML Bulk Load:</span></span>  
  
-   <span data-ttu-id="966ad-104">一括読み込み操作をトランザクションとして実行するよう指定するときには、`TempFilePath` プロパティを使用して、一時ファイルを作成するフォルダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="966ad-104">When you specify that the Bulk Load operation is to be performed as a transaction, you use the `TempFilePath` property to specify a folder in which to create the temporary files.</span></span>  
  
     <span data-ttu-id="966ad-105">一括読み込み処理では、次の権限付きの一時ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="966ad-105">The Bulk Load process creates these temporary files with the following permissions:</span></span>  
  
    -   <span data-ttu-id="966ad-106">読み取り、書き込み、削除アクセス。一括読み込み処理に許可されます。</span><span class="sxs-lookup"><span data-stu-id="966ad-106">Read/Write/Delete access is granted to the Bulk Load process.</span></span>  
  
    -   <span data-ttu-id="966ad-107">読み取り権限。これらのファイルに Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がアクセスするときのアカウントは不明であるため、この権限はすべてのユーザーに許可されます。</span><span class="sxs-lookup"><span data-stu-id="966ad-107">Read permission is granted to all users, because the account under which Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will access these files is unknown.</span></span> <span data-ttu-id="966ad-108">一時ファイルを格納するフォルダーに適切な権限を設定することで、これらの一時ファイルへのアクセスを制限できます。</span><span class="sxs-lookup"><span data-stu-id="966ad-108">You can restrict the access to these temporary files by setting the appropriate permissions on the folder that contains them.</span></span>  
  
-   <span data-ttu-id="966ad-109">XML 一括読み込み自体には権限の設定はありません。</span><span class="sxs-lookup"><span data-stu-id="966ad-109">XML Bulk Load does not itself have any permissions settings.</span></span> <span data-ttu-id="966ad-110">ここでは、データベースが正しく設定され、ユーザー コンテキスト (一括読み込みを使用するよう設定されているログイン) に適切な権限が設定されていることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="966ad-110">It is assumed that the database is set up correctly and that the user context (that is, the login that Bulk Load is set use) has appropriate permissions set.</span></span>  
  
-   <span data-ttu-id="966ad-111">トランザクション以外のモードで一括読み込みの処理中にエラーが発生した場合は、データが部分的に読み込まれたままになることがあります。</span><span class="sxs-lookup"><span data-stu-id="966ad-111">In non-transactional mode, if an error occurs during the Bulk Load process, data may be left in a partially loaded state.</span></span> <span data-ttu-id="966ad-112">一括読み込み処理は、エラーが発生した時点で停止するだけです。</span><span class="sxs-lookup"><span data-stu-id="966ad-112">Bulk Load will simply stop at the point where it is when this happens.</span></span> <span data-ttu-id="966ad-113">この問題を軽減するには、トランザクション モードを使用します。</span><span class="sxs-lookup"><span data-stu-id="966ad-113">Transactional mode can be used to alleviate this issue.</span></span>  
  
-   <span data-ttu-id="966ad-114">一括読み込みで発生するエラーには、データベースに関する情報が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="966ad-114">When Bulk Load errors occur, they may include information about the database.</span></span> <span data-ttu-id="966ad-115">たとえば、テーブルまたは列の名前や、列の型情報が含まれることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="966ad-115">For example, they may include the name of a table or column, or column type information.</span></span> <span data-ttu-id="966ad-116">一括読み込みを使用するときには、一括読み込み処理でエラーを検出して一般的なエラー メッセージを返すように設計し、ユーザーに直接エラーが表示されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="966ad-116">When you use Bulk Load, you should take care to catch errors from the Bulk Load process and return a generic error message, rather than exposing errors directly to users.</span></span>  
  
-   <span data-ttu-id="966ad-117">一括読み込みで処理されるデータ量に制限は設定されていません。</span><span class="sxs-lookup"><span data-stu-id="966ad-117">Bulk Load sets no limit on the amount of data it works over.</span></span> <span data-ttu-id="966ad-118">一括読み込みでは、読み込むデータのサイズはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="966ad-118">Bulk Load does not do any checking on the size of the data to be loaded.</span></span> <span data-ttu-id="966ad-119">一括読み込みを実行するユーザーは、自身の責任で、指定したファイルの処理に必要なメモリを確保し、読み込むデータの格納に必要な空き領域がデータベースにあるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="966ad-119">It is the responsibility of the user executing Bulk Load to ensure that there is enough memory to process the specified file, and that there is enough room in the database to store the data being loaded.</span></span>  
  
-   <span data-ttu-id="966ad-120">一括読み込みでは、コードとして提供されたデータは使用されず、</span><span class="sxs-lookup"><span data-stu-id="966ad-120">Bulk Load does not make an attempt to use the data it is given as code.</span></span> <span data-ttu-id="966ad-121">データ入力はどのような形式でも実行されません。</span><span class="sxs-lookup"><span data-stu-id="966ad-121">The data input is never executed in any fashion.</span></span> <span data-ttu-id="966ad-122">入力データ内のコードまたはコマンドは、通常のデータとして扱われ、実行されることはありません。</span><span class="sxs-lookup"><span data-stu-id="966ad-122">Any code or commands in the input data are treated as normal data and will not be executed.</span></span>  
  
-   <span data-ttu-id="966ad-123">一括読み込みでは、XML と [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ モデルの違いに基づき、指定されたデータの形式が変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="966ad-123">Bulk Load may make formatting changes to the given data based on differences between the XML and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data models.</span></span> <span data-ttu-id="966ad-124">たとえば、時間を指定する形式はこれら 2 つで異なるため、</span><span class="sxs-lookup"><span data-stu-id="966ad-124">For example, the format for specifying a time is different.</span></span> <span data-ttu-id="966ad-125">一括読み込みではこの違いの解決が試みられます。</span><span class="sxs-lookup"><span data-stu-id="966ad-125">Bulk Load will attempt to resolve these differences.</span></span> <span data-ttu-id="966ad-126">この結果、一部の精度情報が失われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="966ad-126">As a result, some precision information may be lost.</span></span>  
  
-   <span data-ttu-id="966ad-127">一括読み込みでは、データ処理は時間の制限なく、</span><span class="sxs-lookup"><span data-stu-id="966ad-127">Bulk Load sets no limit on the amount of time it takes to process the data.</span></span> <span data-ttu-id="966ad-128">処理が完了するかエラーが発生するまで続けられます。</span><span class="sxs-lookup"><span data-stu-id="966ad-128">Processing will continue until processing is complete or an error occurs.</span></span>  
  
-   <span data-ttu-id="966ad-129">一括読み込みでは、データベース内の一時テーブルを作成および削除できます。したがって、このための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="966ad-129">Bulk Load can create and delete temporary tables within the database, and needs permissions to do so.</span></span> <span data-ttu-id="966ad-130">これらのテーブルに対する権限は、一括読み込み処理のためデータベースに接続している同じユーザーに与えられます。</span><span class="sxs-lookup"><span data-stu-id="966ad-130">Permissions to these tables will be given to the same user who is connecting to the database for the Bulk Load process.</span></span>  
  
-   <span data-ttu-id="966ad-131">一括読み込みでは、トランザクション モードでの処理中に使用される一時ファイルを作成および削除できます。したがって、このための権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="966ad-131">Bulk Load can create and delete temporary files used during transactional mode processing, and needs permissions to do so.</span></span> <span data-ttu-id="966ad-132">これらのファイルには、作成時、一括読み込みが実行されているスレッドの現在のユーザーと同じ権限が与えられます。</span><span class="sxs-lookup"><span data-stu-id="966ad-132">These files are created with the same permissions as the current user of the thread within which Bulk Load is running.</span></span>  
  
-   <span data-ttu-id="966ad-133">ユーザーが、エラーを書き込む SQLXML のエラー ログ ファイルを設定した場合は、一括読み込みが実行されるたびに、最新の一括読み込み処理のデータでファイルの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="966ad-133">If the user sets an error Log file for SQLXML to write errors into, then each time Bulk Load is executed the file will be overwritten with data from the last Bulk Load process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966ad-134">参照</span><span class="sxs-lookup"><span data-stu-id="966ad-134">See Also</span></span>  
 [<span data-ttu-id="966ad-135">XML データの一括読み込みの実行 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="966ad-135">Performing Bulk Load of XML Data &#40;SQLXML 4.0&#41;</span></span>](../bulk-load-xml/performing-bulk-load-of-xml-data-sqlxml-4-0.md)  
  
  
