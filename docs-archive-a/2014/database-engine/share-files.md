---
title: ファイルの共有 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- sharing files
- file sharing [SQL Server]
- version control services [SQL Server], file sharing
ms.assetid: 645f5c0a-e949-4e87-8988-85e4d6128464
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 79909fcdb09e349798edfe285475f8a898c3bf04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741221"
---
# <a name="share-files"></a><span data-ttu-id="e2213-102">ファイル共有</span><span class="sxs-lookup"><span data-stu-id="e2213-102">Share Files</span></span>
  <span data-ttu-id="e2213-103">[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、ソース管理プロジェクト間で項目を共有できます。</span><span class="sxs-lookup"><span data-stu-id="e2213-103">You can use [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to share items across source control projects.</span></span> <span data-ttu-id="e2213-104">項目を共有すると、1 つの項目に対する変更は、その項目を共有するすべてのプロジェクトに反映されます。</span><span class="sxs-lookup"><span data-stu-id="e2213-104">When you share an item, any changes to the item are reflected in every project to which the item is shared.</span></span>  
  
 <span data-ttu-id="e2213-105">項目を共有すると、ソース管理のユーザーにとって以下のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="e2213-105">Item sharing provides the following advantages to source control users:</span></span>  
  
-   <span data-ttu-id="e2213-106">共有項目を使用する各プロジェクトでは、項目のコピーを個別に格納する必要がなくなり、ソース管理クライアントおよびサーバーでディスク容量を節約できます。</span><span class="sxs-lookup"><span data-stu-id="e2213-106">Makes it unnecessary for each project that uses the shared item to store a separate copy of the item, conserving disk space on both the source control client and server.</span></span> <span data-ttu-id="e2213-107">ソース管理プロバイダーは、中心となる 1 つの場所に共有項目を格納し、項目を共有している各プロジェクトは、その場所へのポインターを格納します。</span><span class="sxs-lookup"><span data-stu-id="e2213-107">The source control provider stores the shared item in one central location, and every project to which it is shared stores a pointer to that location.</span></span>  
  
-   <span data-ttu-id="e2213-108">バージョンの非互換性を回避できます。</span><span class="sxs-lookup"><span data-stu-id="e2213-108">Avoids version incompatibilities.</span></span> <span data-ttu-id="e2213-109">項目を共有している各プロジェクトでは、項目の同じバージョンを使用するため、複数のプロジェクト内で各項目のコピーが個別に変更された場合に発生する競合を回避できます。</span><span class="sxs-lookup"><span data-stu-id="e2213-109">Because every project to which the item is shared uses the same version of the item, you avoid the conflicts that arise when each copy of an item is changing independently within multiple projects.</span></span>  
  
### <a name="to-share-an-item"></a><span data-ttu-id="e2213-110">項目を共有するには</span><span class="sxs-lookup"><span data-stu-id="e2213-110">To share an item</span></span>  
  
1.  <span data-ttu-id="e2213-111">ソリューション エクスプローラーで、共有ファイルを配置するフォルダーまたはプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e2213-111">In Solution Explorer, select either the folder or project in which you want to place the shared files.</span></span>  
  
2.  <span data-ttu-id="e2213-112">[**ファイル**] メニューの [**ソース管理**] をポイントし、[**共有**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2213-112">On the **File** menu, point to **Source Control**, and then click **Share**.</span></span>  
  
3.  <span data-ttu-id="e2213-113">[**共有**する] ダイアログボックスで、共有する項目のディレクトリ一覧を参照し、その項目をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2213-113">In the **Share with** dialog box, browse the directory list for the item you want to share, and click that item.</span></span>  
  
4.  <span data-ttu-id="e2213-114">**[共有]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e2213-114">Click **Share**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2213-115">参照</span><span class="sxs-lookup"><span data-stu-id="e2213-115">See Also</span></span>  
 [<span data-ttu-id="e2213-116">ソース管理の基礎</span><span class="sxs-lookup"><span data-stu-id="e2213-116">Source Control Basics</span></span>](../../2014/database-engine/source-control-basics.md)  
  
  
