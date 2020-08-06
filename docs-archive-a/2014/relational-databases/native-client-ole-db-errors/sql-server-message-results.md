---
title: SQL Server のメッセージ結果 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
ms.assetid: 6663c6f9-def1-4d9e-845b-2085e5efc401
author: rothja
ms.author: jroth
ms.openlocfilehash: aa63445b81ec89b87523fa29c50817e128d48515
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643800"
---
# <a name="sql-server-message-results"></a><span data-ttu-id="80ba2-102">SQL Server のメッセージ結果</span><span class="sxs-lookup"><span data-stu-id="80ba2-102">SQL Server Message Results</span></span>
  <span data-ttu-id="80ba2-103">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの行セット、または実行時に影響を受ける行の数を生成しません。</span><span class="sxs-lookup"><span data-stu-id="80ba2-103">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] statements do not generate [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider rowsets or a count of affected rows when executed:</span></span>  
  
-   <span data-ttu-id="80ba2-104">PRINT</span><span class="sxs-lookup"><span data-stu-id="80ba2-104">PRINT</span></span>  
  
-   <span data-ttu-id="80ba2-105">重大度が 10 以下の RAISERROR</span><span class="sxs-lookup"><span data-stu-id="80ba2-105">RAISERROR with a severity of 10 or lower</span></span>  
  
-   <span data-ttu-id="80ba2-106">DBCC</span><span class="sxs-lookup"><span data-stu-id="80ba2-106">DBCC</span></span>  
  
-   <span data-ttu-id="80ba2-107">SET SHOWPLAN</span><span class="sxs-lookup"><span data-stu-id="80ba2-107">SET SHOWPLAN</span></span>  
  
-   <span data-ttu-id="80ba2-108">SET STATISTICS</span><span class="sxs-lookup"><span data-stu-id="80ba2-108">SET STATISTICS</span></span>  
  
 <span data-ttu-id="80ba2-109">上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] から情報メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="80ba2-109">These statements either return one or more informational messages or cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to return informational messages in place of rowset or count results.</span></span> <span data-ttu-id="80ba2-110">正常に実行される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と、Native client OLE DB プロバイダーは S_OK を返します。メッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーコンシューマーが使用できます。</span><span class="sxs-lookup"><span data-stu-id="80ba2-110">On successful execution, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK, and the messages are available to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer.</span></span>  
  
 <span data-ttu-id="80ba2-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native client OLE DB プロバイダーは S_OK を返し、多くのステートメントの実行後、 [!INCLUDE[tsql](../../includes/tsql-md.md)] または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native client OLE DB プロバイダーメンバー関数のコンシューマー実行に従って、1つまたは複数の情報メッセージを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="80ba2-111">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns S_OK and has one or more informational messages available following the execution of many [!INCLUDE[tsql](../../includes/tsql-md.md)] statements or the consumer execution of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider member function.</span></span>  
  
 <span data-ttu-id="80ba2-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーコンシューマーは、クエリテキストを動的に指定できるようにするため、リターンコードの値、返される**IRowset**または**IMultipleResults**インターフェイス参照の有無、または影響を受ける行の数に関係なく、すべてのメンバー関数の実行後にエラーインターフェイスをチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="80ba2-112">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider consumer allowing dynamic specification of query text should check error interfaces after every member function execution regardless of the value of the return code, the presence or absence of a returned **IRowset** or **IMultipleResults** interface reference, or a count of affected rows.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ba2-113">参照</span><span class="sxs-lookup"><span data-stu-id="80ba2-113">See Also</span></span>  
 [<span data-ttu-id="80ba2-114">エラー</span><span class="sxs-lookup"><span data-stu-id="80ba2-114">Errors</span></span>](errors.md)  
  
  
