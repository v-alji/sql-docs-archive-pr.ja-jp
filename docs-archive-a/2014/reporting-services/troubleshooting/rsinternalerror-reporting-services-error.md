---
title: rsInternalError - Reporting Services エラー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- rsInternalError
ms.assetid: 52613d52-fc78-4870-93f0-7d393ab9c335
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 85b88519df810f60c580ad2d6eb355dde236d081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641422"
---
# <a name="rsinternalerror---reporting-services-error"></a><span data-ttu-id="22dca-102">rsInternalError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="22dca-102">rsInternalError - Reporting Services Error</span></span>
    
## <a name="details"></a><span data-ttu-id="22dca-103">詳細</span><span class="sxs-lookup"><span data-stu-id="22dca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22dca-104">製品名</span><span class="sxs-lookup"><span data-stu-id="22dca-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="22dca-105">イベント ID</span><span class="sxs-lookup"><span data-stu-id="22dca-105">Event ID</span></span>|<span data-ttu-id="22dca-106">rsInternalError</span><span class="sxs-lookup"><span data-stu-id="22dca-106">rsInternalError</span></span>|  
|<span data-ttu-id="22dca-107">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="22dca-107">Event Source</span></span>|<span data-ttu-id="22dca-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span><span class="sxs-lookup"><span data-stu-id="22dca-108">Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings</span></span>|  
|<span data-ttu-id="22dca-109">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="22dca-109">Component</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|<span data-ttu-id="22dca-110">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="22dca-110">Message Text</span></span>|<span data-ttu-id="22dca-111">レポート サーバーで内部エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="22dca-111">An internal error occurred on the report server.</span></span> <span data-ttu-id="22dca-112">詳細については、エラー ログを参照してください。</span><span class="sxs-lookup"><span data-stu-id="22dca-112">See the error log for more details.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22dca-113">説明</span><span class="sxs-lookup"><span data-stu-id="22dca-113">Explanation</span></span>  
 <span data-ttu-id="22dca-114">これは一般的なエラー メッセージです。多くの場合、このメッセージの後に詳細を示す説明的なエラーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="22dca-114">This is a generic error message that is often followed by a more descriptive error that provides more detail.</span></span>  
  
 <span data-ttu-id="22dca-115">内部エラーが発生するのはまれです。</span><span class="sxs-lookup"><span data-stu-id="22dca-115">Internal errors are uncommon.</span></span> <span data-ttu-id="22dca-116">このエラーが発生した場合は、レポート サーバーのトレース ログで詳細情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="22dca-116">If you get this error, more information is available in report server trace logs.</span></span> <span data-ttu-id="22dca-117">さらに、このエラーが発生したコンピューターで、ローカル管理者として処理を実行している場合は、呼び出し履歴で詳細情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="22dca-117">In addition, if you are running as local administrator on the same computer on which the error occurs, you can view the call stack for more information.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22dca-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="22dca-118">User Action</span></span>  
 <span data-ttu-id="22dca-119">このメッセージの具体的な原因を特定するには、レポートサーバーのログファイルを確認します。これは、\Microsoft SQL サーバーのログファイルにあります。 \<instancename >\ レポート Services\logfiles</span><span class="sxs-lookup"><span data-stu-id="22dca-119">To determine the specific cause for this message, review the report server log files, which are located at \Microsoft SQL Server\MSRS12.\<instancename >\Reporting Services\LogFiles.</span></span> <span data-ttu-id="22dca-120">詳細については、「 [Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22dca-120">For more information, see [Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md).</span></span>  
  
 <span data-ttu-id="22dca-121">呼び出し履歴を表示するには、エラーが発生したページを右クリックし、 **[ソースの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="22dca-121">To view the call stack, right-click the page on which the error occurs and point to **View Source**.</span></span> <span data-ttu-id="22dca-122">呼び出し履歴を表示するには、エラーが発生したコンピューターの管理者権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="22dca-122">Viewing the call stack requires administrator permissions on the same computer on which the error occurs.</span></span>  
  
 <span data-ttu-id="22dca-123">入手できる情報が他にない場合は、再度要求してください。</span><span class="sxs-lookup"><span data-stu-id="22dca-123">If there is no additional information available, you can try your request again.</span></span>  
  
## <a name="internal-only"></a><span data-ttu-id="22dca-124">内部使用のみ</span><span class="sxs-lookup"><span data-stu-id="22dca-124">Internal-Only</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22dca-125">参照</span><span class="sxs-lookup"><span data-stu-id="22dca-125">See Also</span></span>  
 [<span data-ttu-id="22dca-126">レポート サーバー サービスの開始と停止</span><span class="sxs-lookup"><span data-stu-id="22dca-126">Start and Stop the Report Server Service</span></span>](../report-server/start-and-stop-the-report-server-service.md)  
  
  
