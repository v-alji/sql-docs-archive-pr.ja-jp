---
title: クエリ エディターでのコードの色分け
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Query Editor [SQL Server Management Studio], color coding
- color coding [Query Editor]
ms.assetid: 802882dc-c997-4e3f-8a01-994bb43169ae
author: rothja
ms.author: jroth
ms.openlocfilehash: f23b37cec051b52082cdb310a134a4603423b8c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634906"
---
# <a name="color-coding-in-query-editors"></a><span data-ttu-id="964c2-102">クエリ エディターでのコードの色分け</span><span class="sxs-lookup"><span data-stu-id="964c2-102">Color Coding in Query Editors</span></span>
  <span data-ttu-id="964c2-103">コード エディターで入力されたテキストにはカテゴリが割り当てられ、それぞれのカテゴリが色分けされます。</span><span class="sxs-lookup"><span data-stu-id="964c2-103">The text entered in the code editors is assigned a category; each category is identified by a color.</span></span> <span data-ttu-id="964c2-104">色分けによってコード内のテキストをすばやく見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="964c2-104">The colors help you quickly find text in your code.</span></span> <span data-ttu-id="964c2-105">たとえば、濃い緑を使用してコメントが目立つようにします。</span><span class="sxs-lookup"><span data-stu-id="964c2-105">For example, comments stand out in dark green.</span></span> <span data-ttu-id="964c2-106">次の表では、最も一般的な色を示します。</span><span class="sxs-lookup"><span data-stu-id="964c2-106">The following table lists the most common colors.</span></span> <span data-ttu-id="964c2-107">**[ツール]** の **[オプション]** メニューを使用して、色とカテゴリの完全な一覧を表示して、独自の配色を構成できます。</span><span class="sxs-lookup"><span data-stu-id="964c2-107">You can view the whole list of colors and their categories, and configure a custom color scheme by using the **Tools**, **Options** menu.</span></span> <span data-ttu-id="964c2-108">既定の色を変更する方法の詳細については、「 [フォントの色、サイズ、およびスタイルを変更する方法](change-font-color-size-and-style.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="964c2-108">For more information about how to change the default colors, see [Change Font Color, Size, and Style](change-font-color-size-and-style.md).</span></span>  
  
## <a name="default-code-colors"></a><span data-ttu-id="964c2-109">コードの既定の色分け</span><span class="sxs-lookup"><span data-stu-id="964c2-109">Default Code Colors</span></span>  
  
|<span data-ttu-id="964c2-110">Color</span><span class="sxs-lookup"><span data-stu-id="964c2-110">Color</span></span>|<span data-ttu-id="964c2-111">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="964c2-111">Category</span></span>|  
|-----------|--------------|  
|<span data-ttu-id="964c2-112">[赤]</span><span class="sxs-lookup"><span data-stu-id="964c2-112">Red</span></span>|<span data-ttu-id="964c2-113">SQL 文字列</span><span class="sxs-lookup"><span data-stu-id="964c2-113">SQL string</span></span>|  
|<span data-ttu-id="964c2-114">緑</span><span class="sxs-lookup"><span data-stu-id="964c2-114">Dark green</span></span>|<span data-ttu-id="964c2-115">解説</span><span class="sxs-lookup"><span data-stu-id="964c2-115">Comment</span></span>|  
|<span data-ttu-id="964c2-116">黒 (背景は銀色)</span><span class="sxs-lookup"><span data-stu-id="964c2-116">Black on silver background</span></span>|<span data-ttu-id="964c2-117">SQLCMD コマンド</span><span class="sxs-lookup"><span data-stu-id="964c2-117">SQLCMD command</span></span>|  
|<span data-ttu-id="964c2-118">赤紫</span><span class="sxs-lookup"><span data-stu-id="964c2-118">Magenta</span></span>|<span data-ttu-id="964c2-119">システム関数</span><span class="sxs-lookup"><span data-stu-id="964c2-119">System function</span></span>|  
|<span data-ttu-id="964c2-120">[緑]</span><span class="sxs-lookup"><span data-stu-id="964c2-120">Green</span></span>|<span data-ttu-id="964c2-121">システム テーブル、ビュー、またはテーブル値関数。</span><span class="sxs-lookup"><span data-stu-id="964c2-121">System table, view, or table-valued function.</span></span> <span data-ttu-id="964c2-122">sys および INFORMATION_SCHEMA のすべてのシステム スキーマ。</span><span class="sxs-lookup"><span data-stu-id="964c2-122">Also, the system schemas sys and INFORMATION_SCHEMA.</span></span>|  
|<span data-ttu-id="964c2-123">青</span><span class="sxs-lookup"><span data-stu-id="964c2-123">Blue</span></span>|<span data-ttu-id="964c2-124">Keyword</span><span class="sxs-lookup"><span data-stu-id="964c2-124">Keyword</span></span>|  
|<span data-ttu-id="964c2-125">青緑</span><span class="sxs-lookup"><span data-stu-id="964c2-125">Teal</span></span>|<span data-ttu-id="964c2-126">行番号またはテンプレート パラメーター</span><span class="sxs-lookup"><span data-stu-id="964c2-126">Line numbers or template parameter</span></span>|  
|<span data-ttu-id="964c2-127">茶色</span><span class="sxs-lookup"><span data-stu-id="964c2-127">Maroon</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="964c2-128">ストアド プロシージャ (stored procedure)</span><span class="sxs-lookup"><span data-stu-id="964c2-128">stored procedure</span></span>|  
|<span data-ttu-id="964c2-129">灰色</span><span class="sxs-lookup"><span data-stu-id="964c2-129">Dark gray</span></span>|<span data-ttu-id="964c2-130">オペレーター</span><span class="sxs-lookup"><span data-stu-id="964c2-130">Operators</span></span>|  
  
## <a name="status-bar"></a><span data-ttu-id="964c2-131">ステータス バー</span><span class="sxs-lookup"><span data-stu-id="964c2-131">Status Bar</span></span>  
 <span data-ttu-id="964c2-132">オブジェクト エクスプローラーで、登録済みサーバーまたは [!INCLUDE[ssDE](../../includes/ssde-md.md)] サーバーが [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターのステータス バーに別の色で表示されるように構成することができます。</span><span class="sxs-lookup"><span data-stu-id="964c2-132">You can configure registered servers or [!INCLUDE[ssDE](../../includes/ssde-md.md)] servers in Object Explorer to have different colors in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor status bar.</span></span> <span data-ttu-id="964c2-133">そうすることで、多くのウィンドウを同時に開いているときに、各エディター ウィンドウがどのサーバーに接続しているかを識別しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="964c2-133">This helps you identify which server each editor window is connected to when you have many windows open at the same time.</span></span> <span data-ttu-id="964c2-134">ステータス バーの色の設定の詳細については、「[ステータス バー &#40;データベース エンジン クエリ エディター&#41;](status-bar-database-engine-query-editor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="964c2-134">For more information about setting status bar colors, see [Status Bar &#40;Database Engine Query Editor&#41;](status-bar-database-engine-query-editor.md).</span></span>  
  
 <span data-ttu-id="964c2-135">エディターの種類によっては、ステータス バーが表示されない場合や、複数の色がサポートされていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="964c2-135">Some types of editors do not display the status bar, or do not support multiple colors.</span></span>  
  
  
