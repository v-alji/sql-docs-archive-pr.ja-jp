---
title: 既定でオフになっている機能 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87752b8760ffc80e80c87ac1132cae36f2f151b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714745"
---
# <a name="features-off-by-default-analysis-services"></a><span data-ttu-id="bcff6-102">既定でオフになっている機能 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="bcff6-102">Features off by default (Analysis Services)</span></span>
  <span data-ttu-id="bcff6-103">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスは、既定でセキュリティ保護されるようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="bcff6-103">An instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is designed to be secure by default.</span></span> <span data-ttu-id="bcff6-104">したがって、セキュリティを損なう可能性のある機能は既定では無効になっています。</span><span class="sxs-lookup"><span data-stu-id="bcff6-104">Therefore, features that might compromise security are disabled by default.</span></span> <span data-ttu-id="bcff6-105">次の機能は、無効状態でインストールされ、使用するときに明示的に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcff6-105">The following features are installed in a disabled state and must specifically be enabled if you want to use them.</span></span>  
  
## <a name="feature-list"></a><span data-ttu-id="bcff6-106">機能一覧</span><span class="sxs-lookup"><span data-stu-id="bcff6-106">Feature List</span></span>  
 <span data-ttu-id="bcff6-107">次の機能を有効にするには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="bcff6-107">To enable the following features, connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="bcff6-108">インスタンス名を右クリックして、 **[ファセット]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bcff6-108">Right-click the instance name and choose **Facets**.</span></span> <span data-ttu-id="bcff6-109">または、次のセクションで説明するように、これらの機能をサーバー プロパティを通して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bcff6-109">Alternatively, you can enable these features through server properties, as described in the next section.</span></span>  
  
-   <span data-ttu-id="bcff6-110">アドホック データ マイニング (OpenRowset) クエリ</span><span class="sxs-lookup"><span data-stu-id="bcff6-110">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="bcff6-111">リンク オブジェクト (リンク先)</span><span class="sxs-lookup"><span data-stu-id="bcff6-111">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="bcff6-112">リンク オブジェクト (リンク元)</span><span class="sxs-lookup"><span data-stu-id="bcff6-112">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="bcff6-113">ローカル接続のみのリッスン</span><span class="sxs-lookup"><span data-stu-id="bcff6-113">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="bcff6-114">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="bcff6-114">User Defined Functions</span></span>  
  
## <a name="server-properties"></a><span data-ttu-id="bcff6-115">サーバーのプロパティ</span><span class="sxs-lookup"><span data-stu-id="bcff6-115">Server properties</span></span>  
 <span data-ttu-id="bcff6-116">既定でオフになっている追加の機能はサーバー プロパティを通して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bcff6-116">Additional features that are off by default can be enabled through server properties.</span></span> <span data-ttu-id="bcff6-117">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]に接続します。</span><span class="sxs-lookup"><span data-stu-id="bcff6-117">Connect to [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="bcff6-118">インスタンス名を右クリックして、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="bcff6-118">Right-click the instance name and choose **Properties**.</span></span> <span data-ttu-id="bcff6-119">**[全般]** をクリックしてから、 **[詳細の表示]** をクリックして、より大きなプロパティ一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="bcff6-119">Click **General**, and then click **Show Advanced** to display a larger property list.</span></span>  
  
-   <span data-ttu-id="bcff6-120">アドホック データ マイニング (OpenRowset) クエリ</span><span class="sxs-lookup"><span data-stu-id="bcff6-120">Ad Hoc Data Mining (OpenRowset) Queries</span></span>  
  
-   <span data-ttu-id="bcff6-121">セッション マイニング モデルを許可 (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="bcff6-121">Allow Session Mining Models (Data Mining)</span></span>  
  
-   <span data-ttu-id="bcff6-122">リンク オブジェクト (リンク先)</span><span class="sxs-lookup"><span data-stu-id="bcff6-122">Linked Objects (To)</span></span>  
  
-   <span data-ttu-id="bcff6-123">リンク オブジェクト (リンク元)</span><span class="sxs-lookup"><span data-stu-id="bcff6-123">Linked Objects (From)</span></span>  
  
-   <span data-ttu-id="bcff6-124">COM ベースのユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="bcff6-124">COM based user-defined functions</span></span>  
  
-   <span data-ttu-id="bcff6-125">フライト レコーダーのトレース定義 (テンプレート)</span><span class="sxs-lookup"><span data-stu-id="bcff6-125">Flight Recorder Trace Definitions (templates).</span></span>  
  
-   <span data-ttu-id="bcff6-126">クエリ ログ</span><span class="sxs-lookup"><span data-stu-id="bcff6-126">Query logging</span></span>  
  
-   <span data-ttu-id="bcff6-127">ローカル接続のみのリッスン</span><span class="sxs-lookup"><span data-stu-id="bcff6-127">Listen Only On Local Connections</span></span>  
  
-   <span data-ttu-id="bcff6-128">バイナリ XML</span><span class="sxs-lookup"><span data-stu-id="bcff6-128">Binary XML</span></span>  
  
-   <span data-ttu-id="bcff6-129">圧縮</span><span class="sxs-lookup"><span data-stu-id="bcff6-129">Compression</span></span>  
  
-   <span data-ttu-id="bcff6-130">グループ アフィニティ。</span><span class="sxs-lookup"><span data-stu-id="bcff6-130">Group affinity.</span></span> <span data-ttu-id="bcff6-131">詳細については、「 [Thread Pool Properties](../server-properties/thread-pool-properties.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcff6-131">See [Thread Pool Properties](../server-properties/thread-pool-properties.md) for details.</span></span>  
  
  
