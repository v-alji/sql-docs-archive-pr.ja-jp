---
title: スクリプト生成ウィザードでサポートされるオブジェクト
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 071eb2cb-f073-41ca-9f4d-11d3b8803495
author: rothja
ms.author: jroth
ms.openlocfilehash: 5ddc1da0d2f87fc12dfbe034a683802f54b7d34f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644424"
---
# <a name="objects-supported-by-the-generate-scripts-wizard"></a><span data-ttu-id="8b1e9-102">スクリプト生成ウィザードでサポートされるオブジェクト</span><span class="sxs-lookup"><span data-stu-id="8b1e9-102">Objects Supported by the Generate Scripts Wizard</span></span>
  <span data-ttu-id="8b1e9-103">スクリプトの生成とパブリッシュ ウィザードは、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]によってサポートされるオブジェクトのサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8b1e9-103">The Generate and Publish Scripts wizard supports a subset of the objects supported by the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span>  
  
## <a name="supported-objects"></a><span data-ttu-id="8b1e9-104">サポート対象のオブジェクト</span><span class="sxs-lookup"><span data-stu-id="8b1e9-104">Supported Objects</span></span>  
 <span data-ttu-id="8b1e9-105">次の表は、スクリプトの生成とパブリッシュ ウィザードでサポートされる、パブリッシュできるオブジェクトの一覧です。</span><span class="sxs-lookup"><span data-stu-id="8b1e9-105">The following table lists the objects that can be published supported by the Generate and Publish Scripts Wizard.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="8b1e9-106">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="8b1e9-106">Application role</span></span>|<span data-ttu-id="8b1e9-107">データベース ロール</span><span class="sxs-lookup"><span data-stu-id="8b1e9-107">Database role</span></span>|<span data-ttu-id="8b1e9-108">スキーマ</span><span class="sxs-lookup"><span data-stu-id="8b1e9-108">Schema</span></span>|<span data-ttu-id="8b1e9-109">ユーザー定義集計</span><span class="sxs-lookup"><span data-stu-id="8b1e9-109">User-defined aggregate</span></span>|<span data-ttu-id="8b1e9-110">ビュー<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b1e9-110">View<sup>1</sup></span></span>|  
|<span data-ttu-id="8b1e9-111">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="8b1e9-111">Assembly</span></span>|<span data-ttu-id="8b1e9-112">DEFAULT 制約</span><span class="sxs-lookup"><span data-stu-id="8b1e9-112">DEFAULT constraint</span></span>|<span data-ttu-id="8b1e9-113">ストアドプロシージャ<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b1e9-113">Stored procedure<sup>1</sup></span></span>|<span data-ttu-id="8b1e9-114">ユーザー定義データ型</span><span class="sxs-lookup"><span data-stu-id="8b1e9-114">User-defined data type</span></span>|<span data-ttu-id="8b1e9-115">XML スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="8b1e9-115">XML schema collection</span></span>|  
|<span data-ttu-id="8b1e9-116">CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="8b1e9-116">CHECK constraint</span></span>|<span data-ttu-id="8b1e9-117">フルテキスト カタログ</span><span class="sxs-lookup"><span data-stu-id="8b1e9-117">Full-text catalog</span></span>|<span data-ttu-id="8b1e9-118">シノニム</span><span class="sxs-lookup"><span data-stu-id="8b1e9-118">Synonym</span></span>|<span data-ttu-id="8b1e9-119">ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="8b1e9-119">User-defined function</span></span>||  
|<span data-ttu-id="8b1e9-120">CLR (共通言語ランタイム) ストアドプロシージャ<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="8b1e9-120">CLR (common language runtime) stored procedure<sup>1</sup></span></span>|<span data-ttu-id="8b1e9-121">インデックス</span><span class="sxs-lookup"><span data-stu-id="8b1e9-121">Index</span></span>|<span data-ttu-id="8b1e9-122">テーブル</span><span class="sxs-lookup"><span data-stu-id="8b1e9-122">Table</span></span>|<span data-ttu-id="8b1e9-123">ユーザー定義テーブル</span><span class="sxs-lookup"><span data-stu-id="8b1e9-123">User-defined table</span></span>||  
|<span data-ttu-id="8b1e9-124">CLR ユーザー定義関数</span><span class="sxs-lookup"><span data-stu-id="8b1e9-124">CLR user-defined function</span></span>|<span data-ttu-id="8b1e9-125">ルール</span><span class="sxs-lookup"><span data-stu-id="8b1e9-125">Rule</span></span>|<span data-ttu-id="8b1e9-126">ユーザー<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="8b1e9-126">User<sup>2</sup></span></span>|<span data-ttu-id="8b1e9-127">ユーザー定義型</span><span class="sxs-lookup"><span data-stu-id="8b1e9-127">User-defined type</span></span>||  
  
 <span data-ttu-id="8b1e9-128"><sup>1</sup>暗号化なしでパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="8b1e9-128"><sup>1</sup> Published without encryption.</span></span>  
  
 <span data-ttu-id="8b1e9-129"><sup>2</sup>データベースに存在するシステムユーザー以外のユーザーはすべてロールとしてパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="8b1e9-129"><sup>2</sup> Any non-system users that exist in the database are published as Roles.</span></span>  
  
  
