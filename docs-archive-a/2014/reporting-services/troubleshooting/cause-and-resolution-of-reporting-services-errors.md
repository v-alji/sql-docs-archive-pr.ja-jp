---
title: Reporting Services エラーの原因と解決方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- messages [Reporting Services]
- errors [Reporting Services]
- troubleshooting [Reporting Services], errors
ms.assetid: 3db0fef3-37f8-40d0-acc7-1928760dc0e9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fa98b9f760485b80f4fa4ac74f3b8008dc3bbec3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715989"
---
# <a name="cause-and-resolution-of-reporting-services-errors"></a><span data-ttu-id="e60fc-102">Reporting Services エラーの原因と解決方法</span><span class="sxs-lookup"><span data-stu-id="e60fc-102">Cause and Resolution of Reporting Services Errors</span></span>
  <span data-ttu-id="e60fc-103">このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]に関連するさまざまなエラーの原因と解決方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e60fc-103">This topic contains cause and resolution information for a number of errors related to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="e60fc-104">このセクションのエラー メッセージ トピックでは、エラー メッセージとその原因、および問題を解決するための対策について説明します。</span><span class="sxs-lookup"><span data-stu-id="e60fc-104">The error message topics in this section provide an explanation of the error message, possible causes, and any actions you can take to correct the problem.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e60fc-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e60fc-105">In This Section</span></span>  
  
|<span data-ttu-id="e60fc-106">エラー</span><span class="sxs-lookup"><span data-stu-id="e60fc-106">Error</span></span>|<span data-ttu-id="e60fc-107">Message</span><span class="sxs-lookup"><span data-stu-id="e60fc-107">Message</span></span>|  
|-----------|-------------|  
|[<span data-ttu-id="e60fc-108">rsAccessedDenied - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="e60fc-108">rsAccessedDenied - Reporting Services Error</span></span>](rsaccesseddenied-reporting-services-error.md)|<span data-ttu-id="e60fc-109">ユーザー 'mydomain\myAccount' には、この操作を行うのに必要な権限が与えられていません。</span><span class="sxs-lookup"><span data-stu-id="e60fc-109">The permissions granted to user 'mydomain\myAccount' are insufficient for performing this operation.</span></span> <span data-ttu-id="e60fc-110">(rsAccessDenied) (ReportingServicesLibrary)。</span><span class="sxs-lookup"><span data-stu-id="e60fc-110">(rsAccessDenied) (ReportingServicesLibrary).</span></span>|  
|[<span data-ttu-id="e60fc-111">rsInternalError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="e60fc-111">rsInternalError - Reporting Services Error</span></span>](rsinternalerror-reporting-services-error.md)|<span data-ttu-id="e60fc-112">レポート サーバーで内部エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e60fc-112">An internal error occurred on the report server.</span></span> <span data-ttu-id="e60fc-113">詳細については、エラー ログを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e60fc-113">See the error log for more details.</span></span>|  
|[<span data-ttu-id="e60fc-114">rsModelGenerationError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="e60fc-114">rsModelGenerationError - Reporting Services Error</span></span>](rsmodelgenerationerror-reporting-services-error.md)|<span data-ttu-id="e60fc-115">モデルの生成中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e60fc-115">An error occurred while generating model.</span></span> <span data-ttu-id="e60fc-116">(rsModelGenerationError) (ReportingServicesLibrary) %1。</span><span class="sxs-lookup"><span data-stu-id="e60fc-116">(rsModelGenerationError) (ReportingServicesLibrary) %1.</span></span>|  
|[<span data-ttu-id="e60fc-117">rsProcessingError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="e60fc-117">rsProcessingError - Reporting Services Error</span></span>](rsprocessingerror-reporting-services-error.md)|<span data-ttu-id="e60fc-118">レポートの処理中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e60fc-118">Errors have occurred in report processing.</span></span>|  
|[<span data-ttu-id="e60fc-119">rsServerConfigurationError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="e60fc-119">rsServerConfigurationError - Reporting Services Error</span></span>](rsserverconfigurationerror-reporting-services-error.md)|<span data-ttu-id="e60fc-120">レポート サーバーで構成エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e60fc-120">The report server has encountered a configuration error.</span></span>|  
|[<span data-ttu-id="e60fc-121">rrRenderingError - Reporting Services エラー</span><span class="sxs-lookup"><span data-stu-id="e60fc-121">rrRenderingError - Reporting Services Error</span></span>](rrrenderingerror-reporting-services-error.md)|<span data-ttu-id="e60fc-122">レポートの表示中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e60fc-122">An error occurred during rendering of the report.</span></span> <span data-ttu-id="e60fc-123">(rrRenderingError) %1。</span><span class="sxs-lookup"><span data-stu-id="e60fc-123">(rrRenderingError) %1.</span></span>|  
|[<span data-ttu-id="e60fc-124">レポート サーバー Windows サービス (MSSQLServer) 107</span><span class="sxs-lookup"><span data-stu-id="e60fc-124">Report Server Windows Service &#40;MSSQLServer&#41; 107</span></span>](../../relational-databases/errors-events/mssqlserver-107-database-engine-error.md)|<span data-ttu-id="e60fc-125">レポート サーバー Windows サービス (MSSQLSERVER) はレポート サーバー データベースに接続できません。</span><span class="sxs-lookup"><span data-stu-id="e60fc-125">Report Server Windows service (MSSQLSERVER) cannot connect to the report server database.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e60fc-126">参照</span><span class="sxs-lookup"><span data-stu-id="e60fc-126">See Also</span></span>  
 <span data-ttu-id="e60fc-127">[Reporting Services のログ ファイルとソース](../report-server/reporting-services-log-files-and-sources.md) </span><span class="sxs-lookup"><span data-stu-id="e60fc-127">[Reporting Services Log Files and Sources](../report-server/reporting-services-log-files-and-sources.md) </span></span>  
 [<span data-ttu-id="e60fc-128">エラーとイベントのリファレンス (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="e60fc-128">Errors and Events Reference &#40;Reporting Services&#41;</span></span>](errors-and-events-reference-reporting-services.md)  
  
  
