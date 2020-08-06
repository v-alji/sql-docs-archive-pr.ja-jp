---
title: パッケージに注釈を追加する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- self-documenting packages
- adding annotations
- annotations [Integration Services]
ms.assetid: 8db31e78-e03b-44e6-a307-a1349f52b0c6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fc482f12328b792c1d0b4262a88a292398d9715
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640225"
---
# <a name="add-an-annotation-to-a-package"></a><span data-ttu-id="25795-102">パッケージに注釈を追加する</span><span class="sxs-lookup"><span data-stu-id="25795-102">Add an Annotation to a Package</span></span>
  <span data-ttu-id="25795-103">この手順では、パッケージに注釈を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="25795-103">This procedure describes how to add an annotation to a package.</span></span>  
  
### <a name="to-add-an-annotation-to-a-package"></a><span data-ttu-id="25795-104">パッケージに注釈を追加するには</span><span class="sxs-lookup"><span data-stu-id="25795-104">To add an annotation to a package</span></span>  
  
1.  <span data-ttu-id="25795-105">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、注釈を追加するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="25795-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package to which you want to add an annotation.</span></span>  
  
2.  <span data-ttu-id="25795-106">ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="25795-106">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="25795-107">[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、 **[制御フロー]** タブ、 **[データ フロー]** タブ、または **[イベント ハンドラー]** タブのデザイン画面上の任意の場所を右クリックし、 **[注釈の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25795-107">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, right-click anywhere on the design surface of the **Control Flow**, **Data Flow**, or **Event Handler** tab, and then click **Add Annotation**.</span></span> <span data-ttu-id="25795-108">タブのデザイン画面に、テキスト ブロックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="25795-108">A text block appears on the design surface of the tab.</span></span>  
  
4.  <span data-ttu-id="25795-109">テキストを追加します。</span><span class="sxs-lookup"><span data-stu-id="25795-109">Add text.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="25795-110">テキストを追加しない場合、ブロックの外側をクリックするとテキスト ブロックは削除されます。</span><span class="sxs-lookup"><span data-stu-id="25795-110">If you add no text, the text block is removed when you click outside the block.</span></span>  
  
5.  <span data-ttu-id="25795-111">注釈内のテキストのサイズまたは書式を変更するには、注釈を右クリックし、 **[テキスト注釈のフォントの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25795-111">To change the size or format of the text in the annotation, right-click the annotation and then click **Set Text Annotation Font**.</span></span>  
  
6.  <span data-ttu-id="25795-112">テキスト行を追加するには、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="25795-112">To add an additional line of text, press ENTER.</span></span>  
  
     <span data-ttu-id="25795-113">テキスト行を追加すると、注釈ボックスのサイズが自動的に大きくなります。</span><span class="sxs-lookup"><span data-stu-id="25795-113">The annotation box automatically increases in size as you add additional lines of text.</span></span>  
  
7.  <span data-ttu-id="25795-114">グループに注釈を追加するには、注釈を右クリックし、 **[グループ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25795-114">To add an annotation to a group, right-click the annotation and then click **Group**.</span></span>  
  
8.  <span data-ttu-id="25795-115">更新したパッケージを保存するには、 **[ファイル]** メニューの **[すべてを保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="25795-115">To save the updated package, on the **File** menu, click **Save All**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25795-116">参照</span><span class="sxs-lookup"><span data-stu-id="25795-116">See Also</span></span>  
 [<span data-ttu-id="25795-117">パッケージで注釈を使用する</span><span class="sxs-lookup"><span data-stu-id="25795-117">Use Annotations in Packages</span></span>](use-annotations-in-packages.md)  
  
  
