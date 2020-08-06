---
title: 画像、テキスト ボックス、四角形、および罫線 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: aa7ad08f-dd49-401e-9619-522e27055bb9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fb9a47bb3b8d68d48be42f8f0a2adddfc3ba130
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713861"
---
# <a name="images-text-boxes-rectangles-and-lines-report-builder-and-ssrs"></a><span data-ttu-id="0779e-102">画像、テキスト ボックス、四角形、および罫線 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="0779e-102">Images, Text Boxes, Rectangles, and Lines (Report Builder and SSRS)</span></span>
  <span data-ttu-id="0779e-103">レポートでは、視覚的な効果の追加、重要な情報の強調、または関連情報の提供のために、テーブル、マトリックス、グラフなどのデータ領域以外にも、画像、テキスト ボックス、四角形などのレポート アイテムが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0779e-103">In addition to data regions like tables, matrices, and charts, reports use other report items like images, text boxes, and rectangles to add visual interest, highlight key information, or provide related information.</span></span> <span data-ttu-id="0779e-104">レポート アイテムの書式設定は変更できます。</span><span class="sxs-lookup"><span data-stu-id="0779e-104">You can change the formatting of a report item.</span></span> <span data-ttu-id="0779e-105">たとえば、罫線または余白の追加、初期表示または方向の変更、またはアイテムの正確なサイズと位置の指定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0779e-105">For example, you can add a border or padding, change the initial visibility or direction, or specify an exact size and location for the item.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="0779e-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0779e-106">In This Section</span></span>  
 [<span data-ttu-id="0779e-107">テキスト ボックス (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="0779e-107">Text Boxes &#40;Report Builder and SSRS&#41;</span></span>](text-boxes-report-builder-and-ssrs.md)  
 <span data-ttu-id="0779e-108">テキスト ボックスは、レポートの任意の場所に配置できます。また、テキスト ボックスには、ラベル、フィールド、計算されたデータを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0779e-108">Text boxes can be placed anywhere on a report and can contain labels, fields, or calculated data.</span></span> <span data-ttu-id="0779e-109">レポートを表示するときにテキスト ボックスに表示する値を定義するには、式を使用します。</span><span class="sxs-lookup"><span data-stu-id="0779e-109">You use expressions to define the value to display in a text box when you view a report.</span></span>  
  
 <span data-ttu-id="0779e-110">テーブルまたはマトリックスの各セルもテキスト ボックスで、スタンドアロン テキスト ボックスと同じ方法で書式設定できます。</span><span class="sxs-lookup"><span data-stu-id="0779e-110">Every cell in a table or matrix is also a text box, which you can format in the same way that you format stand-alone text boxes.</span></span>  
  
 [<span data-ttu-id="0779e-111">四角形と線 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0779e-111">Rectangles and Lines &#40;Report Builder and SSRS&#41;</span></span>](rectangles-and-lines-report-builder-and-ssrs.md)  
 <span data-ttu-id="0779e-112">**罫線** は、水平方向、垂直方向、または対角線方向に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0779e-112">**Lines** display horizontally, vertically, or diagonally.</span></span> <span data-ttu-id="0779e-113">罫線は始点と終点で定義します。また、さまざまなスタイル (太さや色など) を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="0779e-113">A line is defined with a start and end point and can have various styles (for example, weight and color) assigned to it.</span></span> <span data-ttu-id="0779e-114">罫線にはデータの割り当ては行われません。</span><span class="sxs-lookup"><span data-stu-id="0779e-114">A line has no data associated with it.</span></span>  
  
 <span data-ttu-id="0779e-115">**四角形** は、グラフィック要素、またはその他のレポート アイテムのコンテナーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="0779e-115">**Rectangles** can be used as a graphical element, or as a container for other report items.</span></span> <span data-ttu-id="0779e-116">グラフィック要素の場合、四角形には罫線と同じプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="0779e-116">As a graphical element, a rectangle has the same properties as a line.</span></span> <span data-ttu-id="0779e-117">コンテナーの場合、四角形は、その中にあるすべてのレポート アイテムの親コンテナーとして機能します。</span><span class="sxs-lookup"><span data-stu-id="0779e-117">As a container, a rectangle acts as a parent container for all report items inside it.</span></span> <span data-ttu-id="0779e-118">親コンテナーにレポート アイテムを配置すると、各レポート ページでのアイテムの表示方法を制御できます。</span><span class="sxs-lookup"><span data-stu-id="0779e-118">Placing report items in a parent container helps control how they appear on each report page.</span></span>  
  
 [<span data-ttu-id="0779e-119">画像 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="0779e-119">Images &#40;Report Builder and SSRS&#41;</span></span>](images-report-builder-and-ssrs.md)  
 <span data-ttu-id="0779e-120">画像には、レポートに含まれる画像のバイナリ データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0779e-120">Images display binary image data in a report.</span></span> <span data-ttu-id="0779e-121">画像のソースを指定します。</span><span class="sxs-lookup"><span data-stu-id="0779e-121">You provide the source for the image.</span></span> <span data-ttu-id="0779e-122">ソースには、Web サーバー上に保存された画像への URL 参照、埋め込み画像データへの参照、またはデータベース内のバイナリの画像データへの参照を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0779e-122">The source can be a URL reference to an image stored on a Web server, a reference to embedded image data, or a reference to binary image data in a database.</span></span> <span data-ttu-id="0779e-123">レポート ビルダーおよびレポート デザイナーでは、.bmp ファイル、.jpeg ファイル、.gif ファイル、および .png ファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0779e-123">Report Builder and Report Designer support .bmp, .jpeg, .gif, and .png files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0779e-124">参照</span><span class="sxs-lookup"><span data-stu-id="0779e-124">See Also</span></span>  
 [<span data-ttu-id="0779e-125">レポート アイテムの書式設定 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="0779e-125">Formatting Report Items &#40;Report Builder and SSRS&#41;</span></span>](formatting-report-items-report-builder-and-ssrs.md)  
  
  
