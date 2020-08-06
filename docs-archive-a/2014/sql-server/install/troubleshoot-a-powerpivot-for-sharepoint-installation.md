---
title: PowerPivot for SharePoint のインストールのトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 3adc27132d976288c14ac702baae0b842e8aef0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640412"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a><span data-ttu-id="23354-102">PowerPivot for SharePoint インストールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="23354-102">Troubleshoot a PowerPivot for SharePoint Installation</span></span>
  <span data-ttu-id="23354-103">予想したページや機能ではなくエラーが表示された場合は、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="23354-103">If you get errors instead of the pages and features you expect, do the following.</span></span>  
  
-   <span data-ttu-id="23354-104">SharePoint と [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の両方のリリース ノートで、インストールの既知の問題を回避する方法を調べます。</span><span class="sxs-lookup"><span data-stu-id="23354-104">Review release notes for both SharePoint and [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to get workarounds for known installation problems.</span></span> <span data-ttu-id="23354-105">リリース ノートは、インストール メディア、またはソフトウェアをダウンロードした Microsoft サイトで提供されています。</span><span class="sxs-lookup"><span data-stu-id="23354-105">Release notes are provided with the installation media or on the Microsoft site from which you downloaded the software.</span></span>  
  
    -   <span data-ttu-id="23354-106">[SQL Server 2014 リリースノート](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="23354-106">[SQL Server 2014 Release Notes](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).</span></span>  
  
-   <span data-ttu-id="23354-107">Technet wiki トピック「 [PowerPivot (およびその他のアドイン) のインストールのトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23354-107">See the Technet wiki topic, [Troubleshooting Installations of PowerPivot (and other add-ins)](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx).</span></span>  
  
## <a name="issues"></a><span data-ttu-id="23354-108">問題</span><span class="sxs-lookup"><span data-stu-id="23354-108">Issues</span></span>  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a><span data-ttu-id="23354-109">PowerPivot ギャラリーのサムネイル画像として赤い X マークが表示される</span><span class="sxs-lookup"><span data-stu-id="23354-109">PowerPivot Gallery Thumbnail images show as a red X</span></span>  
 <span data-ttu-id="23354-110">考えられる原因の1つは、**サイトコレクションの PowerPivot 機能の統合**がアクティブではないことです。</span><span class="sxs-lookup"><span data-stu-id="23354-110">One Possible cause is the **PowerPivot features Integration for Site Collections** is not active.</span></span> <span data-ttu-id="23354-111">次の作業を完了します。</span><span class="sxs-lookup"><span data-stu-id="23354-111">Complete the following:</span></span>  
  
1.  <span data-ttu-id="23354-112">PowerPivot ギャラリーライブラリで、歯車アイコン![SharePoint の設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")または**ホーム**リストから [サイトの**設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23354-112">In the PowerPivot Gallery library, click **Site Settings** from either the gear icon ![SharePoint Settings](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint Settings") or the **Home** list.</span></span>  
  
2.  <span data-ttu-id="23354-113">**[サイト コレクションの管理]** セクションで **[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23354-113">In the **Site Collection Administration** section, click **Site Collection Features**.</span></span>  
  
3.  <span data-ttu-id="23354-114">**[サイト コレクションの機能]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="23354-114">Click **Site Collection Features**.</span></span>  
  
4.  <span data-ttu-id="23354-115">**サイトコレクションの PowerPivot 機能の統合**が**アクティブ**であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="23354-115">Verify **PowerPivot features Integration for Site Collections** is **Active**.</span></span>  
  
 <span data-ttu-id="23354-116">この問題のその他の原因については、「 [PowerPivot ギャラリーのアイコン](https://support.microsoft.com/kb/2361559)()」を参照してください https://support.microsoft.com/kb/2361559) 。</span><span class="sxs-lookup"><span data-stu-id="23354-116">For additional causes of this issue, see [PowerPivot Gallery shows Red X's for Icons](https://support.microsoft.com/kb/2361559) (https://support.microsoft.com/kb/2361559).</span></span>  
  
  
