---
title: オプション (SQL Server AlwaysOn、[ダッシュボード] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Alwayson.Dashboard
ms.assetid: 4369b588-e982-4b57-80a1-beb2e879ce0b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bef7622b56aabb2c908337fef4d110a12dd5a9bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634642"
---
# <a name="options-sql-server-alwayson-dashboard-page"></a><span data-ttu-id="31f21-102">オプション (SQLServer AlwaysOn、ダッシュ ボード ページ)</span><span class="sxs-lookup"><span data-stu-id="31f21-102">Options (SQL Server AlwaysOn, Dashboard Page)</span></span>
  <span data-ttu-id="31f21-103">[オプション] ダイアログボックスの [ **SQL Server Alwayson ダッシュボード**] ページを使用して、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] **Options** alwayson ダッシュボードを構成します。</span><span class="sxs-lookup"><span data-stu-id="31f21-103">Use the **SQL Server AlwaysOn Dashboard** page of the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the AlwaysOn Dashboard.</span></span>  
  
 <span data-ttu-id="31f21-104">**このページにアクセスするには:**</span><span class="sxs-lookup"><span data-stu-id="31f21-104">**To access this page:**</span></span>  
  
 <span data-ttu-id="31f21-105">[**ツール**] メニューの [**オプション**] をクリックし、 **SQL Server AlwaysOn**フォルダーを展開して、[**ダッシュボード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31f21-105">On the **Tools** menu, click **Options**, expand the **SQL Server AlwaysOn** folder, and then click **Dashboard**.</span></span>  
  
## <a name="on-this-page"></a><span data-ttu-id="31f21-106">このページの内容</span><span class="sxs-lookup"><span data-stu-id="31f21-106">On This Page</span></span>  
 <span data-ttu-id="31f21-107">**[自動更新を有効にする]**</span><span class="sxs-lookup"><span data-stu-id="31f21-107">**Turn on automatic refresh.**</span></span>  
 <span data-ttu-id="31f21-108">クリックすると、自動更新が有効になります。</span><span class="sxs-lookup"><span data-stu-id="31f21-108">Click to enable automatic refresh.</span></span> <span data-ttu-id="31f21-109">オプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="31f21-109">The options are:</span></span>  
  
-   <span data-ttu-id="31f21-110">**[更新間隔 (秒単位)]** フィールドには、ダッシュボードが更新される秒数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31f21-110">The **Refresh interval (in seconds)** field displays the number of seconds at which the dashboard will refresh.</span></span> <span data-ttu-id="31f21-111">既定値は 30 です。</span><span class="sxs-lookup"><span data-stu-id="31f21-111">The default value is 30.</span></span> <span data-ttu-id="31f21-112">自動更新を有効にすると、このフィールドを編集して更新間隔を変更できます。</span><span class="sxs-lookup"><span data-stu-id="31f21-112">When automatic refresh is enabled, you can edit this field to change the refresh interval.</span></span>  
  
-   <span data-ttu-id="31f21-113">**[接続の再試行回数]** には、ダッシュボードが監視している可用性グループの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスにダッシュボードが接続を試行する回数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="31f21-113">The **Number of connection retries** displays the number of times that the dashboard will attempt to connect to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica for an availability group that the Dashboard is monitoring.</span></span> <span data-ttu-id="31f21-114">既定値は、65535 です。</span><span class="sxs-lookup"><span data-stu-id="31f21-114">The default value is 65535.</span></span> <span data-ttu-id="31f21-115">自動更新を有効にすると、このフィールドを編集して接続試行回数を変更できます。</span><span class="sxs-lookup"><span data-stu-id="31f21-115">When automatic refresh is enabled, you can edit this field to change the number of connection retries.</span></span>  
  
 <span data-ttu-id="31f21-116">**[ユーザー定義の AlwaysOn ポリシーを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="31f21-116">**Enable your user-defined AlwaysOn policy.**</span></span>  
 <span data-ttu-id="31f21-117">AlwaysOn ポリシーを定義している場合は、このオプションをクリックしてポリシーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="31f21-117">If you have defined your own AlwaysOn policy, click this option to enable your policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f21-118">参照</span><span class="sxs-lookup"><span data-stu-id="31f21-118">See Also</span></span>  
 [<span data-ttu-id="31f21-119">AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="31f21-119">Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;</span></span>](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
