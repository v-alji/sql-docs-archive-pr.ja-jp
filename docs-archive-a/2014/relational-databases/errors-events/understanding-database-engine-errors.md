---
title: データベース エンジン エラーについて | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], about errors
- errors [SQL Server], Database Engine
- errors [SQL Server]
- Database Engine [SQL Server], errors
ms.assetid: ddaca9d3-956f-46a5-8cd3-a7a15ec75878
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa8747066433488a8517d2931ad51f082075a66f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641654"
---
# <a name="understanding-database-engine-errors"></a><span data-ttu-id="d9733-102">データベース エンジン エラーについて</span><span class="sxs-lookup"><span data-stu-id="d9733-102">Understanding Database Engine Errors</span></span>
  <span data-ttu-id="d9733-103">次の表で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] によって発生したエラーの属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="d9733-103">Errors raised by the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] have the attributes described in the following table.</span></span>  
  
|<span data-ttu-id="d9733-104">属性</span><span class="sxs-lookup"><span data-stu-id="d9733-104">Attribute</span></span>|<span data-ttu-id="d9733-105">説明</span><span class="sxs-lookup"><span data-stu-id="d9733-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9733-106">エラー番号</span><span class="sxs-lookup"><span data-stu-id="d9733-106">Error number</span></span>|<span data-ttu-id="d9733-107">エラー メッセージには、それぞれ一意なエラー番号が付いています。</span><span class="sxs-lookup"><span data-stu-id="d9733-107">Each error message has a unique error number.</span></span>|  
|<span data-ttu-id="d9733-108">エラー メッセージ文字列</span><span class="sxs-lookup"><span data-stu-id="d9733-108">Error message string</span></span>|<span data-ttu-id="d9733-109">エラー メッセージには、エラーの原因についての診断情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d9733-109">The error message contains diagnostic information about the cause of the error.</span></span> <span data-ttu-id="d9733-110">多くのエラー メッセージには、エラーが発生したオブジェクト名などの情報を挿入するための置換変数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d9733-110">Many error messages have substitution variables in which information, such as the name of the object generating the error, is inserted.</span></span>|  
|<span data-ttu-id="d9733-111">重大度</span><span class="sxs-lookup"><span data-stu-id="d9733-111">Severity</span></span>|<span data-ttu-id="d9733-112">重大度レベルは、エラーの重大度を示します。</span><span class="sxs-lookup"><span data-stu-id="d9733-112">The severity indicates how serious the error is.</span></span> <span data-ttu-id="d9733-113">1、2 など重大度レベルが低いエラーは情報メッセージ、または低レベル警告です。</span><span class="sxs-lookup"><span data-stu-id="d9733-113">Errors that have a low severity, such as 1 or 2, are information messages or low-level warnings.</span></span> <span data-ttu-id="d9733-114">重大度レベルが高いエラーは、できるだけ早く対処することが推奨される問題であることを示します。</span><span class="sxs-lookup"><span data-stu-id="d9733-114">Errors that have a high severity indicate problems that should be addressed as soon as possible.</span></span> <span data-ttu-id="d9733-115">重大度レベルの詳細については、「 [データベース エンジン エラーの重大度](database-engine-error-severities.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9733-115">For more information about severities, see [Database Engine Error Severities](database-engine-error-severities.md).</span></span>|  
|<span data-ttu-id="d9733-116">State</span><span class="sxs-lookup"><span data-stu-id="d9733-116">State</span></span>|<span data-ttu-id="d9733-117">エラー メッセージが [!INCLUDE[ssDE](../../includes/ssde-md.md)]のコード内の複数の場所で生成される場合があります。</span><span class="sxs-lookup"><span data-stu-id="d9733-117">Some error messages can be raised at multiple points in the code for the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="d9733-118">たとえば、複数の異なる条件に対して 1105 エラーが生成されることがあります。</span><span class="sxs-lookup"><span data-stu-id="d9733-118">For example, an 1105 error can be raised for several different conditions.</span></span> <span data-ttu-id="d9733-119">エラーを生成する特定の条件はそれぞれ一意の状態コードを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d9733-119">Each specific condition that raises an error assigns a unique state code.</span></span><br /><br /> <span data-ttu-id="d9733-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] のサポート技術情報など既知の問題に関する情報が含まれたデータベースを参照する場合は、状態番号を使用して、記録された問題と検出されたエラーが同じかどうかを判断することができます。</span><span class="sxs-lookup"><span data-stu-id="d9733-120">When you are viewing databases that contain information about known issues, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Knowledge Base, you can use the state number to determine whether the recorded issue is the same as the error you have encountered.</span></span> <span data-ttu-id="d9733-121">たとえば、サポート技術情報の記事が状態 2 の 1105 エラーについて説明しており、受け取った 1105 エラー メッセージが状態 3 の場合、このエラーは記事で報告されているエラーとは原因が異なる可能性が高いと考えられます。</span><span class="sxs-lookup"><span data-stu-id="d9733-121">For example, if a Knowledge Base Article describes an 1105 error that has a state of 2 and the 1105 error message you received had a state of 3, the error probably has a different cause than the one reported in the article.</span></span><br /><br /> <span data-ttu-id="d9733-122">[!INCLUDE[msCoName](../../includes/msconame-md.md)] のサポート エンジニアがこのエラーの状態コードを使用して、エラー コードが生成されたソース コード内の場所を探すこともできます。</span><span class="sxs-lookup"><span data-stu-id="d9733-122">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] support engineer can also use the state code from an error to find the location in the source code where that error code is being raised.</span></span> <span data-ttu-id="d9733-123">この情報が、問題に対する他の診断方法のヒントになる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d9733-123">This information might provide additional ideas on how to diagnose the problem.</span></span>|  
|<span data-ttu-id="d9733-124">プロシージャ名</span><span class="sxs-lookup"><span data-stu-id="d9733-124">Procedure name</span></span>|<span data-ttu-id="d9733-125">エラーが発生したストアド プロシージャまたはトリガーの名前です。</span><span class="sxs-lookup"><span data-stu-id="d9733-125">Is the name of the stored procedure or trigger in which the error has occurred.</span></span>|  
|<span data-ttu-id="d9733-126">行番号</span><span class="sxs-lookup"><span data-stu-id="d9733-126">Line number</span></span>|<span data-ttu-id="d9733-127">バッチ、ストアド プロシージャ、トリガー、または関数内のどのステートメントでエラーが発生したかを示します。</span><span class="sxs-lookup"><span data-stu-id="d9733-127">Indicates which statement in a batch, stored procedure, trigger, or function generated the error.</span></span>|  
  
 <span data-ttu-id="d9733-128">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のインスタンス内のすべてのシステム エラー メッセージおよびユーザー定義のエラー メッセージは、 **sys.messages** カタログ ビューに含まれています。</span><span class="sxs-lookup"><span data-stu-id="d9733-128">All system and user-defined error messages in an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] are contained in the **sys.messages** catalog view.</span></span> <span data-ttu-id="d9733-129">RAISERROR ステートメントを使用すると、アプリケーションにユーザー定義エラーを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="d9733-129">You can use the RAISERROR statement to return user-defined errors to an application.</span></span>  
  
 <span data-ttu-id="d9733-130">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** 名前空間、ActiveX Data Objects (ADO)、OLE DB、Open Database Connectivity (ODBC) などのすべてのデータベース API で、基本的なエラー属性が報告されます。</span><span class="sxs-lookup"><span data-stu-id="d9733-130">All database APIs, such as the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] **SQLClient** namespace, ActiveX Data Objects (ADO), OLE DB, and Open Database Connectivity (ODBC), report the basic error attributes.</span></span> <span data-ttu-id="d9733-131">この情報には、エラー番号およびメッセージ文字列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d9733-131">This information includes the error number and message string.</span></span> <span data-ttu-id="d9733-132">ただし、すべての API で他のすべてのエラー属性が報告されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d9733-132">However, not all the APIs report all the other error attributes.</span></span>  
  
 <span data-ttu-id="d9733-133">TRY...CATCH 構造の TRY ブロックの適用範囲内で発生したエラーの詳細は、関連付けられた CATCH ブロックの適用範囲内で ERROR_LINE、ERROR_MESSAGE、ERROR_NUMBER、ERROR_PROCEDURE、ERROR_SEVERITY、ERROR_STATE などの関数を使用して [!INCLUDE[tsql](../../includes/tsql-md.md)] コードで取得することができます。</span><span class="sxs-lookup"><span data-stu-id="d9733-133">Information about an error that occurs in the scope of the TRY block of a TRY...CATCH construct can be obtained in [!INCLUDE[tsql](../../includes/tsql-md.md)] code by using functions such as ERROR_LINE, ERROR_MESSAGE, ERROR_NUMBER, ERROR_PROCEDURE, ERROR_SEVERITY, and ERROR_STATE in the scope of the associated CATCH block.</span></span> <span data-ttu-id="d9733-134">詳細については、「 [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9733-134">For more information, see [TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d9733-135">例</span><span class="sxs-lookup"><span data-stu-id="d9733-135">Examples</span></span>  
 <span data-ttu-id="d9733-136">次の例では、 `sys.messages` カタログ ビューにクエリを実行し、英語テキスト ( [!INCLUDE[ssDE](../../includes/ssde-md.md)] ) が含まれた`1033`内のシステム エラー メッセージおよびユーザー定義のエラー メッセージがすべて記載された一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="d9733-136">The following example queries the `sys.messages` catalog view to return a list of all system and user-defined error messages in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that have English text (`1033`).</span></span>  
  
```  
SELECT  
    message_id,  
    language_id,  
    severity,  
    is_event_logged,  
    text  
  FROM sys.messages  
  WHERE language_id = 1033;  
```  
  
 <span data-ttu-id="d9733-137">詳細については、「 [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d9733-137">For more information, see [sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9733-138">参照</span><span class="sxs-lookup"><span data-stu-id="d9733-138">See Also</span></span>  
 <span data-ttu-id="d9733-139">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span><span class="sxs-lookup"><span data-stu-id="d9733-139">[sys.messages &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) </span></span>  
 <span data-ttu-id="d9733-140">[RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-140">[RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql) </span></span>  
 <span data-ttu-id="d9733-141">[@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-141">[@@ERROR &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-transact-sql) </span></span>  
 <span data-ttu-id="d9733-142">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-142">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span></span>  
 <span data-ttu-id="d9733-143">[ERROR_LINE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-143">[ERROR_LINE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-line-transact-sql) </span></span>  
 <span data-ttu-id="d9733-144">[ERROR_MESSAGE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-144">[ERROR_MESSAGE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-message-transact-sql) </span></span>  
 <span data-ttu-id="d9733-145">[ERROR_NUMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-145">[ERROR_NUMBER &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-number-transact-sql) </span></span>  
 <span data-ttu-id="d9733-146">[ERROR_PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-146">[ERROR_PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-procedure-transact-sql) </span></span>  
 <span data-ttu-id="d9733-147">[ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d9733-147">[ERROR_SEVERITY &#40;Transact-SQL&#41;](/sql/t-sql/functions/error-severity-transact-sql) </span></span>  
 [<span data-ttu-id="d9733-148">ERROR_STATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d9733-148">ERROR_STATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/error-state-transact-sql)  
  
  
