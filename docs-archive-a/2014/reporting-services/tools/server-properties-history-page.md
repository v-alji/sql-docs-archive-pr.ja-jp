---
title: '[サーバーのプロパティ] ([履歴] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.serverproperties.history.f1
ms.assetid: be9d8018-a46f-4625-9ae1-138ebe6b38ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: df5ff9dc7a94431f8feec112d460938aa1631ef2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641973"
---
# <a name="server-properties-history-page"></a><span data-ttu-id="99f6e-102">[サーバーのプロパティ]\([履歴] ページ)</span><span class="sxs-lookup"><span data-stu-id="99f6e-102">Server Properties (History Page)</span></span>
  <span data-ttu-id="99f6e-103">このページを使用すると、保持されるレポート履歴のコピー数の既定値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-103">Use this page to set a default value for the number of copies of report history to retain.</span></span> <span data-ttu-id="99f6e-104">既定値には、すべてのレポートのレポート履歴の制限を規定する初期設定が用意されています。</span><span class="sxs-lookup"><span data-stu-id="99f6e-104">The default value provides an initial setting that establishes report history limits for all reports.</span></span> <span data-ttu-id="99f6e-105">これらの設定は、レポートごとに変えることができます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-105">You can vary these settings for individual reports.</span></span>  
  
 <span data-ttu-id="99f6e-106">レポート履歴は、スナップショット作成時点のレポートで最新だったレポート データとレイアウトが含まれるレポート スナップショットを集めたものです。</span><span class="sxs-lookup"><span data-stu-id="99f6e-106">Report history is a collection of report snapshots that include report data and layout that is current for the report at the time the snapshot is created.</span></span> <span data-ttu-id="99f6e-107">レポート履歴を使用すると、特定の日時の状態でレポートのコピーを保持できます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-107">You can use report history to keep a copy of a report as it was on a specific date or time.</span></span> <span data-ttu-id="99f6e-108">ネイティブ モードのレポート サーバーまたは SharePoint 統合モード用に構成されたレポート サーバーで実行される個別のレポートについて、レポート履歴を作成および管理することができます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-108">You can create and manage report history for individual reports that run on a native mode report server or a report server that is configured for SharePoint integrated mode.</span></span>  
  
 <span data-ttu-id="99f6e-109">レポート履歴スナップショットは、レポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-109">Report history snapshots are stored in the report server database.</span></span> <span data-ttu-id="99f6e-110">スナップショットを無制限に保持する場合は、データベース サイズが急速に増大したり、ディスク領域が過度に消費されていないかどうかを定期的に確認してください。</span><span class="sxs-lookup"><span data-stu-id="99f6e-110">If you keep an unlimited number of snapshots, be sure to periodically check the database size to ensure it is not growing too fast or consuming too much disk space.</span></span>  
  
 <span data-ttu-id="99f6e-111">このページを開くには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動してレポート サーバー インスタンスに接続し、レポート サーバー名を右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="99f6e-111">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server instance, right-click the report server name, and select **Properties**.</span></span> <span data-ttu-id="99f6e-112">**[履歴]** をクリックすると、このページが開きます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-112">Click **History** to open this page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="99f6e-113">Options</span><span class="sxs-lookup"><span data-stu-id="99f6e-113">Options</span></span>  
 <span data-ttu-id="99f6e-114">**[レポート履歴に無制限の数のスナップショットを保持する]**</span><span class="sxs-lookup"><span data-stu-id="99f6e-114">**Keep an unlimited number of snapshots in report history**</span></span>  
 <span data-ttu-id="99f6e-115">すべてのレポート履歴スナップショットを保持します。</span><span class="sxs-lookup"><span data-stu-id="99f6e-115">Retain all report history snapshots.</span></span> <span data-ttu-id="99f6e-116">このレポート ヒストリのサイズを減らすには、スナップショットを手動で削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99f6e-116">You must manually delete snapshots to reduce the size of report history.</span></span>  
  
 <span data-ttu-id="99f6e-117">**[レポート履歴のコピーの数を制限する]**</span><span class="sxs-lookup"><span data-stu-id="99f6e-117">**Limit the copies of report history**</span></span>  
 <span data-ttu-id="99f6e-118">設定された数のレポート履歴スナップショットを保持します。</span><span class="sxs-lookup"><span data-stu-id="99f6e-118">Retain a set number of report history snapshots.</span></span> <span data-ttu-id="99f6e-119">制限値に達すると、古いコピーはレポート ヒストリから順次削除され、空いた領域に新しいコピーが保存されます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-119">When the limit is reached, older copies are removed from report history to make room for newer copies.</span></span>  
  
 <span data-ttu-id="99f6e-120">これから指定するレポート履歴の制限を超えてから、既存のレポート履歴を制限した場合、既存のレポート履歴が新しい制限値まで削減されます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-120">If you limit report history later, when the existing report history exceeds the limit you specify, the report server reduces the existing report history to the new limit.</span></span> <span data-ttu-id="99f6e-121">最初に、最も古いレポート スナップショットが削除されます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-121">The oldest report snapshots are deleted first.</span></span> <span data-ttu-id="99f6e-122">レポート履歴が空であるか、制限を超えていない場合は、新しいレポート スナップショットが追加されます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-122">If report history is empty or below the limit, new report snapshots are added.</span></span> <span data-ttu-id="99f6e-123">制限に達すると、新しいレポート スナップショットが追加されたときに最も古いスナップショットが削除されます。</span><span class="sxs-lookup"><span data-stu-id="99f6e-123">When the limit is reached, the oldest snapshot is deleted when a new report snapshot is added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f6e-124">参照</span><span class="sxs-lookup"><span data-stu-id="99f6e-124">See Also</span></span>  
 <span data-ttu-id="99f6e-125">[レポートサーバーのプロパティ &#40;Management Studio の設定&#41;](set-report-server-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="99f6e-125">[Set Report Server Properties &#40;Management Studio&#41;](set-report-server-properties-management-studio.md) </span></span>  
 <span data-ttu-id="99f6e-126">[Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="99f6e-126">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="99f6e-127">Management Studio のレポート サーバーの F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="99f6e-127">Report Server in Management Studio F1 Help</span></span>](report-server-in-management-studio-f1-help.md)  
  
  
