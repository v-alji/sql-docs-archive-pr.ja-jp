---
title: ストアドプロシージャの実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, stored procedures
- stored procedures [ODBC], running
- SQL Server Native Client ODBC driver, stored procedures
- stored procedures [ODBC], executing
ms.assetid: 866b6dd3-2acd-4dfb-aeca-a0352b2d4c6a
author: rothja
ms.author: jroth
ms.openlocfilehash: 8e5de6a9a13c95b417657a1d108403fa27abe34b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741946"
---
# <a name="running-stored-procedures"></a><span data-ttu-id="afa6b-102">ストアド プロシージャの実行</span><span class="sxs-lookup"><span data-stu-id="afa6b-102">Running Stored Procedures</span></span>
  <span data-ttu-id="afa6b-103">ストアド プロシージャは、データベースに保存される実行可能なオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="afa6b-103">A stored procedure is an executable object stored in a database.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="afa6b-104">では次に示すオブジェクトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="afa6b-104">supports:</span></span>  
  
-   <span data-ttu-id="afa6b-105">ストアド プロシージャ:</span><span class="sxs-lookup"><span data-stu-id="afa6b-105">Stored procedures:</span></span>  
  
     <span data-ttu-id="afa6b-106">1 つの実行可能なプロシージャとしてプリコンパイルされた 1 つ以上の SQL ステートメント。</span><span class="sxs-lookup"><span data-stu-id="afa6b-106">One or more SQL statements precompiled into a single executable procedure.</span></span>  
  
-   <span data-ttu-id="afa6b-107">拡張ストアド プロシージャ : </span><span class="sxs-lookup"><span data-stu-id="afa6b-107">Extended stored procedures:</span></span>  
  
     <span data-ttu-id="afa6b-108">拡張ストアド プロシージャ用の SQL Server オープン データ サービス API に記述された、C または C++ のダイナミック リンク ライブラリ (DLL)。</span><span class="sxs-lookup"><span data-stu-id="afa6b-108">C or C++ dynamic-link libraries (DLL) written to the SQL Server Open Data Services API for extended stored procedures.</span></span> <span data-ttu-id="afa6b-109">オープン データ サービス API によりストアド プロシージャの機能が拡張され、C または C++ のコードを実装できるようになります。</span><span class="sxs-lookup"><span data-stu-id="afa6b-109">The Open Data Services API extends the capabilities of stored procedures to include C or C++ code.</span></span>  
  
 <span data-ttu-id="afa6b-110">ステートメントの実行時、データ ソースに対して (クライアント アプリケーション内でステートメントを直接実行または準備せずに) ストアド プロシージャを呼び出すと、次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="afa6b-110">When executing statements, calling a stored procedure on the data source (instead of directly executing or preparing a statement in the client application) can provide:</span></span>  
  
-   <span data-ttu-id="afa6b-111">パフォーマンスが高い</span><span class="sxs-lookup"><span data-stu-id="afa6b-111">Higher performance</span></span>  
  
     <span data-ttu-id="afa6b-112">SQL ステートメントは、プロシージャが作成される時点で、解析およびコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-112">SQL statements are parsed and compiled when procedures are created.</span></span> <span data-ttu-id="afa6b-113">プロシージャの実行時には、これらの作業は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="afa6b-113">This overhead is then saved when the procedures are executed.</span></span>  
  
-   <span data-ttu-id="afa6b-114">ネットワーク オーバーヘッドの軽減</span><span class="sxs-lookup"><span data-stu-id="afa6b-114">Reduced network overhead</span></span>  
  
     <span data-ttu-id="afa6b-115">複雑なクエリをネットワーク経由で送信するのではなく、プロシージャを実行することで、ネットワーク トラフィックを削減できます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-115">Executing a procedure instead of sending complex queries across the network can reduce network traffic.</span></span> <span data-ttu-id="afa6b-116">ODBC アプリケーションが ODBC { CALL } 構文を使用してストアド プロシージャを実行すると、ODBC ドライバーがさらに最適化を行い、パラメーター データの変換が不要になります。</span><span class="sxs-lookup"><span data-stu-id="afa6b-116">If an ODBC application uses the ODBC { CALL } syntax to execute a stored procedure, the ODBC driver makes additional optimizations that eliminate the need to convert parameter data.</span></span>  
  
-   <span data-ttu-id="afa6b-117">整合性の向上</span><span class="sxs-lookup"><span data-stu-id="afa6b-117">Greater consistency</span></span>  
  
     <span data-ttu-id="afa6b-118">組織の規則がストアド プロシージャなどの 1 つのリソースに集約して実装されると、コーディング、テスト、デバッグを一度で行えます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-118">If an organization's rules are implemented in a central resource, such as a stored procedure, they can be coded, tested, and debugged once.</span></span> <span data-ttu-id="afa6b-119">各プログラマが独自の実装を開発するのではなく、テスト済みの共通のストアド プロシージャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-119">Individual programmers can then use the tested stored procedures instead of developing their own implementations.</span></span>  
  
-   <span data-ttu-id="afa6b-120">精度の向上</span><span class="sxs-lookup"><span data-stu-id="afa6b-120">Greater accuracy</span></span>  
  
     <span data-ttu-id="afa6b-121">通常、ストアド プロシージャは経験を積んだプログラマが開発するので、技術レベルの異なるプログラマが繰り返し手を加えたコードに比べて、効率的でエラーが少なくなる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="afa6b-121">Because stored procedures are usually developed by experienced programmers, they tend to be more efficient and have fewer errors than code developed multiple times by programmers of varying skill levels.</span></span>  
  
-   <span data-ttu-id="afa6b-122">機能の追加</span><span class="sxs-lookup"><span data-stu-id="afa6b-122">Added functionality</span></span>  
  
     <span data-ttu-id="afa6b-123">拡張ストアド プロシージャは、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントでは使用できない C や C++ の機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="afa6b-123">Extended stored procedures can use C and C++ features not available in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="afa6b-124">ストアドプロシージャを呼び出す方法の例については、「 [&#40;ODBC&#41;のリターンコードと出力パラメーターの処理](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afa6b-124">For an example of how to call a stored procedure, see [Process Return Codes and Output Parameters &#40;ODBC&#41;](../native-client-odbc-how-to/running-stored-procedures-process-return-codes-and-output-parameters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afa6b-125">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="afa6b-125">In This Section</span></span>  
  
-   [<span data-ttu-id="afa6b-126">ストアド プロシージャの呼び出し</span><span class="sxs-lookup"><span data-stu-id="afa6b-126">Calling a Stored Procedure</span></span>](calling-a-stored-procedure.md)  
  
-   [<span data-ttu-id="afa6b-127">ストアド プロシージャ呼び出しのバッチ化</span><span class="sxs-lookup"><span data-stu-id="afa6b-127">Batching Stored Procedure Calls</span></span>](batching-stored-procedure-calls.md)  
  
-   [<span data-ttu-id="afa6b-128">ストアド プロシージャの結果の処理</span><span class="sxs-lookup"><span data-stu-id="afa6b-128">Processing Stored Procedure Results</span></span>](processing-stored-procedure-results.md)  
  
## <a name="see-also"></a><span data-ttu-id="afa6b-129">参照</span><span class="sxs-lookup"><span data-stu-id="afa6b-129">See Also</span></span>  
 <span data-ttu-id="afa6b-130">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="afa6b-130">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 [<span data-ttu-id="afa6b-131">ストアドプロシージャの実行方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="afa6b-131">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
