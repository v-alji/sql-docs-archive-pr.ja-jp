---
title: エラーページ (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8311ed32-00f3-451d-8279-946429f5fee1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fc50a5b0516bcbf8221ce3ee130090f66a929c3e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719616"
---
# <a name="error-page-report-manager"></a><span data-ttu-id="f674c-102">[エラー] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="f674c-102">Error Page (Report Manager)</span></span>
  <span data-ttu-id="f674c-103">[エラー] ページには、エラーの状況に関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f674c-103">Use the Error page to view details about an error condition.</span></span> <span data-ttu-id="f674c-104">このページには、サーバーベースまたはセッションベースのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f674c-104">Server-based or session-based errors appear on this page.</span></span> <span data-ttu-id="f674c-105">特定のページ コントロールに関連する検証エラーは、コントロールの横にインラインで表示されます。</span><span class="sxs-lookup"><span data-stu-id="f674c-105">Validation errors that relate to specific page controls display inline next to the control.</span></span>  
  
-   <span data-ttu-id="f674c-106">ローカルレポートサーバーを参照しているときに、次のようなエラーが表示される場合は、「[ローカル管理用のネイティブモードのレポートサーバーを構成する &#40;SSRS](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md) 」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="f674c-106">If you are browsing to a local report server and you see errors similar to the following, see: [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)</span></span>  
  
     <span data-ttu-id="f674c-107">ユーザー ' Domain \\ [user name] ' に必要なアクセス許可がありません。</span><span class="sxs-lookup"><span data-stu-id="f674c-107">User 'Domain\\[user name]' does not have required permissions.</span></span> <span data-ttu-id="f674c-108">適切なアクセス許可が付与されていることと、Windows ユーザー アカウント制御 (UAC) の制限に対処済みであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f674c-108">Verify that sufficient permissions have been granted and Windows User Account Control (UAC) restrictions have been addressed.</span></span>  
  
-   <span data-ttu-id="f674c-109">次のようなエラー メッセージが表示された場合は、「 [Configure a Report Server for Remote Administration](report-server/configure-a-report-server-for-remote-administration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f674c-109">If you see error messages similar to the following, see [Configure a Report Server for Remote Administration](report-server/configure-a-report-server-for-remote-administration.md).</span></span>  
  
     <span data-ttu-id="f674c-110">コンピューターが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f674c-110">The machine could not be found.</span></span> <span data-ttu-id="f674c-111">"RPC サーバーを利用できません。</span><span class="sxs-lookup"><span data-stu-id="f674c-111">"The RPC server is unavailable.</span></span> <span data-ttu-id="f674c-112">(HRESULT からの例外: 0x800706BA)"。</span><span class="sxs-lookup"><span data-stu-id="f674c-112">(Exception from HRESULT: 0x800706BA)".</span></span>  
  
-   <span data-ttu-id="f674c-113">リモート サーバーで発生するエラー状態に関する追加情報が返されるように、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーのサーバー プロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="f674c-113">You can set server properties on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server to return additional information about error conditions that occur on remote servers.</span></span> <span data-ttu-id="f674c-114">エラーメッセージに "このエラーの詳細については、ローカルサーバーコンピューター上のレポートサーバーに移動するか、リモートエラーを有効にする" というテキストが含まれている場合は、「 [Enable Remote errors &#40;Reporting Services&#41;](report-server/enable-remote-errors-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f674c-114">If an error message contains the text "For more information about this error, navigate to the report server on the local server machine, or enable remote errors", see [Enable Remote Errors &#40;Reporting Services&#41;](report-server/enable-remote-errors-reporting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f674c-115">参照</span><span class="sxs-lookup"><span data-stu-id="f674c-115">See Also</span></span>  
 <span data-ttu-id="f674c-116">[レポートマネージャー &#40;ネイティブモード&#41;を構成する](report-server/configure-web-portal.md) </span><span class="sxs-lookup"><span data-stu-id="f674c-116">[Configure Report Manager &#40;Native Mode&#41;](report-server/configure-web-portal.md) </span></span>  
 <span data-ttu-id="f674c-117">[エラーとイベントのリファレンス &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f674c-117">[Errors and Events Reference &#40;Reporting Services&#41;](troubleshooting/errors-and-events-reference-reporting-services.md) </span></span>  
 [<span data-ttu-id="f674c-118">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="f674c-118">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
