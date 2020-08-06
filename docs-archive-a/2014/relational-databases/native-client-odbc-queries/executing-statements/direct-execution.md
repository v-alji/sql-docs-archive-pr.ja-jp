---
title: 直接実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC applications, statements
- direct execution [ODBC]
- SQLExecDirect function
- statements [ODBC], direct execution
ms.assetid: fa36e1af-ed98-4abc-97c1-c4cc5d227b29
author: rothja
ms.author: jroth
ms.openlocfilehash: 29153f3e4e9265e87feb0e23ba9ae97118691e95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631869"
---
# <a name="direct-execution"></a><span data-ttu-id="d440b-102">直接実行</span><span class="sxs-lookup"><span data-stu-id="d440b-102">Direct Execution</span></span>
  <span data-ttu-id="d440b-103">直接実行はステートメントを実行する最も基本的な方法です。</span><span class="sxs-lookup"><span data-stu-id="d440b-103">Direct execution is the most basic way to execute a statement.</span></span> <span data-ttu-id="d440b-104">アプリケーションは、ステートメントを含む文字列を構築 [!INCLUDE[tsql](../../../includes/tsql-md.md)] し、 **SQLExecDirect**関数を使用して実行するために送信します。</span><span class="sxs-lookup"><span data-stu-id="d440b-104">An application builds a character string containing a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement and submits it for execution using the **SQLExecDirect** function.</span></span> <span data-ttu-id="d440b-105">ステートメントがサーバーに到達すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がステートメントを実行プランにコンパイルしてから、すぐにその実行プランを実行します。</span><span class="sxs-lookup"><span data-stu-id="d440b-105">When the statement reaches the server, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compiles it into an execution plan and then immediately runs the execution plan.</span></span>  
  
 <span data-ttu-id="d440b-106">直接実行は、通常、実行時にステートメントを構築して実行するアプリケーションで使用され、1 回だけステートメントを実行する場合には最も効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="d440b-106">Direct execution is commonly used by applications that build and execute statements at run time and is the most efficient method for statements that will be executed a single time.</span></span> <span data-ttu-id="d440b-107">多くのデータベースでの直接実行の欠点は、SQL ステートメントを実行するたびに解析とコンパイルが必要なことで、ステートメントを複数回実行する場合はオーバーヘッドが増加します。</span><span class="sxs-lookup"><span data-stu-id="d440b-107">Its drawback with many databases is that the SQL statement must be parsed and compiled each time it is executed, which adds overhead if the statement is executed multiple times.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="d440b-108">では、マルチユーザー環境で通常実行されるステートメントに関して、直接実行のパフォーマンスが大幅に向上します。また、通常、SQL ステートメントの実行にパラメーター マーカーを指定して SQLExecDirect を使用すると、準備実行に近い効率を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="d440b-108">significantly improves the performance of direct execution of commonly executed statements in multiuser environments and using SQLExecDirect with parameter markers for commonly executed SQL statements can approach the efficiency of prepared execution.</span></span>  
  
 <span data-ttu-id="d440b-109">のインスタンスに接続されている場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC ドライバーは、 [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql)を使用して、 **SQLExecDirect**で指定された SQL ステートメントまたはバッチを転送します。</span><span class="sxs-lookup"><span data-stu-id="d440b-109">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver uses [sp_executesql](/sql/relational-databases/system-stored-procedures/sp-executesql-transact-sql) to transmit the SQL statement or batch specified on **SQLExecDirect**.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="d440b-110">には、 **sp_executesql**で実行された SQL ステートメントまたはバッチが、既にメモリに存在する実行プランを生成したステートメントまたはバッチと一致するかどうかをすばやく判断するロジックがあります。</span><span class="sxs-lookup"><span data-stu-id="d440b-110">has logic to quickly determine if an SQL statement or batch executed with **sp_executesql** matches the statement or batch that generated an execution plan that already exists in memory.</span></span> <span data-ttu-id="d440b-111">一致する場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は新しいプランをコンパイルしないで、単に既存のプランを再利用します。</span><span class="sxs-lookup"><span data-stu-id="d440b-111">If a match is made, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] simply reuses the existing plan rather than compile a new plan.</span></span> <span data-ttu-id="d440b-112">これは、多くのユーザーがいるシステムで**SQLExecDirect**を使用して実行される一般的に実行される SQL ステートメントが、以前のバージョンののストアドプロシージャでしか使用できなかった、プラン再利用の多くの利点を活用できることを意味し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="d440b-112">This means that commonly executed SQL statements executed with **SQLExecDirect** in a system with many users will benefit from many of the plan-reuse benefits that were only available to stored procedures in earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="d440b-113">実行プランを再利用することで得られる利点は、複数のユーザーが同じ SQL ステートメントやバッチを実行しているときにのみ効果があります。</span><span class="sxs-lookup"><span data-stu-id="d440b-113">This benefit of reusing execution plans only works when several users are executing the same SQL statement or batch.</span></span> <span data-ttu-id="d440b-114">異なるクライアントが実行する SQL ステートメントを可能な限り統一の取れたステートメントにして、実行プランの再利用を可能にするために、次のコーディング規則に従ってください。</span><span class="sxs-lookup"><span data-stu-id="d440b-114">Follow these coding conventions to increase the probability that the SQL statements executed by different clients are similar enough to be able to reuse execution plans:</span></span>  
  
-   <span data-ttu-id="d440b-115">SQL ステートメントには定数データを含めません。代わりにプログラム変数にバインドされるパラメーター マーカーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d440b-115">Do not include data constants in the SQL statements; instead use parameter markers bound to program variables.</span></span> <span data-ttu-id="d440b-116">詳細については、「[ステートメントパラメーターの使用](../using-statement-parameters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d440b-116">For more information, see [Using Statement Parameters](../using-statement-parameters.md).</span></span>  
  
-   <span data-ttu-id="d440b-117">完全修飾オブジェクト名を使用します。</span><span class="sxs-lookup"><span data-stu-id="d440b-117">Use fully qualified object names.</span></span> <span data-ttu-id="d440b-118">実行プランは、オブジェクト名が修飾されていないと再利用されません。</span><span class="sxs-lookup"><span data-stu-id="d440b-118">Execution plans are not reused if object names are not qualified.</span></span>  
  
-   <span data-ttu-id="d440b-119">アプリケーション接続では、できる限り、接続オプションとステートメント オプションの共通のセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="d440b-119">Have application connections as possible use a common set of connection and statement options.</span></span> <span data-ttu-id="d440b-120">あるオプションのセット (ANSI_NULLS など) を使用する接続に対して生成される実行プランは、別のオプションのセットを使用する接続には再利用されません。</span><span class="sxs-lookup"><span data-stu-id="d440b-120">Execution plans generated for a connection with one set of options (such as ANSI_NULLS) are not reused for a connection having another set of options.</span></span> <span data-ttu-id="d440b-121">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、どちらもこれらのオプションに同じ既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="d440b-121">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider both have the same default settings for these options.</span></span>  
  
 <span data-ttu-id="d440b-122">**SQLExecDirect**で実行されたすべてのステートメントがこれらの規則を使用してコード化されている場合、では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 営業案件が発生したときに実行プランを再利用</span><span class="sxs-lookup"><span data-stu-id="d440b-122">If all statements executed with **SQLExecDirect** are coded using these conventions, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can reuse execution plans when the opportunity arises.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d440b-123">参照</span><span class="sxs-lookup"><span data-stu-id="d440b-123">See Also</span></span>  
 [<span data-ttu-id="d440b-124">ODBC&#41;&#40;のステートメントの実行</span><span class="sxs-lookup"><span data-stu-id="d440b-124">Executing Statements &#40;ODBC&#41;</span></span>](executing-statements-odbc.md)  
  
  
