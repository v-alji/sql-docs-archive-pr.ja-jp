---
title: SharePoint ライブラリへのレポートの保存 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4daa1eee-78b7-43d0-8b22-4a98e8fa66ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 49878a0d7115a11e804382cb5139aa0ec7b3d254
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640738"
---
# <a name="save-a-report-to-a-sharepoint-library-report-builder"></a><span data-ttu-id="84b85-102">SharePoint ライブラリへのレポートの保存 (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="84b85-102">Save a Report to a SharePoint Library (Report Builder)</span></span>
  <span data-ttu-id="84b85-103">SharePoint 統合用に構成されているレポート サーバーにレポートを保存するには、SharePoint サーバーを参照して、レポート サーバーへの接続を確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84b85-103">To save a report to a report server configured for SharePoint integration, you must browse to the SharePoint server and establish a connection to the report server.</span></span> <span data-ttu-id="84b85-104">レポート定義では、レポートに関連するアイテムへのすべての参照で、SharePoint レポート サーバー固有の値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84b85-104">In the report definition, all references to items related to the report must use values that are specific to a SharePoint report server.</span></span> <span data-ttu-id="84b85-105">関連するアイテムには、サブレポート、詳細レポート、および Web ベースの画像などのリソースがあります。</span><span class="sxs-lookup"><span data-stu-id="84b85-105">Related items include subreports, drillthrough reports, and resources such as Web-based images.</span></span> <span data-ttu-id="84b85-106">詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="84b85-106">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](../report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="84b85-107">プロジェクトにプロパティを設定するには、SharePoint サイトの **メンバー** 権限または **所有者** 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="84b85-107">You must have **Member** or **Owner** permission on the SharePoint site to set the properties on the project.</span></span>  
  
### <a name="to-save-a-report-to-a-sharepoint-site"></a><span data-ttu-id="84b85-108">SharePoint サイトにレポートを保存するには</span><span class="sxs-lookup"><span data-stu-id="84b85-108">To save a report to a SharePoint site</span></span>  
  
1.  <span data-ttu-id="84b85-109">レポート ビルダーのボタンの **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b85-109">From the Report Builder button, click **Save**.</span></span> <span data-ttu-id="84b85-110">[**名前を付けて保存** _\<Report Item>_ ] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84b85-110">The **Save As**_\<Report Item>_ dialog box opens.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84b85-111">レポートを再保存すると、自動的に以前の場所に再保存されます。</span><span class="sxs-lookup"><span data-stu-id="84b85-111">If you are resaving a report, it is automatically resaved to its previous location.</span></span> <span data-ttu-id="84b85-112">場所を変更するには、 **[名前を付けて保存]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="84b85-112">Use the **Save As** option to change location.</span></span>  
  
2.  <span data-ttu-id="84b85-113">必要に応じて、 **[最近使ったサイトとサーバー]** をクリックし、最近使用したレポート サーバーと SharePoint サイトの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="84b85-113">Optionally, click **Recent Sites and Servers** to show a list of recently used report servers and SharePoint sites.</span></span>  
  
3.  <span data-ttu-id="84b85-114">SharePoint サイトを参照して指定し、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b85-114">Browse to the SharePoint site, and then click **Save**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="84b85-115">レポートを変更した後、保存せずに 10 時間経過すると、サーバーから切断されます。変更内容は保存されません。</span><span class="sxs-lookup"><span data-stu-id="84b85-115">If you leave a changed report for more than 10 hours without saving it, it is disconnected from the server without being saved.</span></span> <span data-ttu-id="84b85-116">その場合は、右下のステータス バーで **[切断]** をクリックしてから **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="84b85-116">If that happens, in the lower-right status bar, click **Disconnect**, and then click **Connect**.</span></span> <span data-ttu-id="84b85-117">使用可能なサーバーのリストに、直近のサーバーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="84b85-117">The most recent server will be in the list of available servers.</span></span> <span data-ttu-id="84b85-118">それを選択すると、レポートが再度接続されます。</span><span class="sxs-lookup"><span data-stu-id="84b85-118">Select it and the report will reconnect.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b85-119">参照</span><span class="sxs-lookup"><span data-stu-id="84b85-119">See Also</span></span>  
 [<span data-ttu-id="84b85-120">レポートの検索、表示、管理 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="84b85-120">Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;</span></span>](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
