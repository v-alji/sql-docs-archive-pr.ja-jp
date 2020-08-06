---
title: '[オプション] ([テキストエディター]/[XML]/[書式設定] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97373178-d288-4127-af37-d9f5fe1b8607
author: rothja
ms.author: jroth
ms.openlocfilehash: dce36142fe9974c0167fca700c509642e05d89b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716581"
---
# <a name="options-text-editor---xml---formatting-page"></a><span data-ttu-id="978c8-102">[オプション] ([テキスト エディター]/[XML]/[書式設定] ページ)</span><span class="sxs-lookup"><span data-stu-id="978c8-102">Options (Text Editor - XML - Formatting Page)</span></span>

<span data-ttu-id="978c8-103">このダイアログ ボックスでは、XML エディターの書式設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="978c8-103">This dialog box allows you to specify the formatting settings for the XML Editor.</span></span> <span data-ttu-id="978c8-104">**[ツール]** メニューから **[オプション]** ダイアログ ボックスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="978c8-104">You can access the **Options** dialog box from the **Tools** menu.</span></span>  
  
> [!NOTE]  
> <span data-ttu-id="978c8-105">次の設定は、**[テキスト エディター]** フォルダーを展開し、**[XML]** フォルダーを展開して、**[オプション]** ダイアログ ボックスの **[書式設定]** オプションを選択したときに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="978c8-105">These settings are available when you select the **Text Editor** folder, the **XML** folder, and then the **Formatting** option from the **Options** dialog box.</span></span>  
  
## <a name="attributes"></a><span data-ttu-id="978c8-106">属性</span><span class="sxs-lookup"><span data-stu-id="978c8-106">Attributes</span></span>  
 <span data-ttu-id="978c8-107">**[手動による属性の書式設定を保持する]**</span><span class="sxs-lookup"><span data-stu-id="978c8-107">**Preserve manual attribute formatting**</span></span>  
 <span data-ttu-id="978c8-108">属性の書式設定を変更しません。</span><span class="sxs-lookup"><span data-stu-id="978c8-108">Do not reformat attributes.</span></span> <span data-ttu-id="978c8-109">既定値です。</span><span class="sxs-lookup"><span data-stu-id="978c8-109">This is the default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="978c8-110">属性が複数行にある場合、エディターは属性の各行にインデントを設定して、親要素のインデントに一致させます。</span><span class="sxs-lookup"><span data-stu-id="978c8-110">If the attributes are on multiple lines, the editor indents each line of attributes to match the indentation of the parent element.</span></span>  
  
 <span data-ttu-id="978c8-111">**[各行の属性の記述位置を揃える]**</span><span class="sxs-lookup"><span data-stu-id="978c8-111">**Align attributes each on a separate line**</span></span>  
 <span data-ttu-id="978c8-112">2 番目以降の属性を縦に配置して、最初の属性のインデントに一致させます。</span><span class="sxs-lookup"><span data-stu-id="978c8-112">Align the second and subsequent attributes vertically to match the indentation of the first attribute.</span></span> <span data-ttu-id="978c8-113">次の XML テキストは、属性を配置する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="978c8-113">The following XML text is an example of how the attributes would be aligned.</span></span>  
  
```  
<item id = "123-A"  
      name = "hammer"  
      price = "9.95"  
</item>  
```  
  
## <a name="auto-reformat"></a><span data-ttu-id="978c8-114">[自動再フォーマット]</span><span class="sxs-lookup"><span data-stu-id="978c8-114">Auto Reformat</span></span>  
 <span data-ttu-id="978c8-115">**[クリップボードからのペースト時]**</span><span class="sxs-lookup"><span data-stu-id="978c8-115">**On paste from clipboard.**</span></span>  
 <span data-ttu-id="978c8-116">クリップボードから貼り付けられる XML テキストの書式設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="978c8-116">Reformat XML text pasted from the clipboard.</span></span>  
  
 <span data-ttu-id="978c8-117">**[終了タグの完了時]**</span><span class="sxs-lookup"><span data-stu-id="978c8-117">**On completion of end tag**</span></span>  
 <span data-ttu-id="978c8-118">終了タグが完了するときに、要素の書式設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="978c8-118">Reformat the element when the end tag is completed.</span></span>  
  
## <a name="mixed-content"></a><span data-ttu-id="978c8-119">混合コンテンツ</span><span class="sxs-lookup"><span data-stu-id="978c8-119">Mixed Content</span></span>  
 <span data-ttu-id="978c8-120">**[混合したコンテンツを既定でフォーマットする]**</span><span class="sxs-lookup"><span data-stu-id="978c8-120">**Format mixed content by default.**</span></span>  
 <span data-ttu-id="978c8-121">コンテンツが `xml:space="preserve"` 範囲内で検出された場合以外は、混合コンテンツの書式設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="978c8-121">Attempt to reformat mixed content, except when the content is found in an `xml:space="preserve"` scope.</span></span> <span data-ttu-id="978c8-122">既定値です。</span><span class="sxs-lookup"><span data-stu-id="978c8-122">This is the default.</span></span>  
  
 <span data-ttu-id="978c8-123">要素にテキストとマークアップが混在している場合、コンテンツは混合コンテンツと見なされます。</span><span class="sxs-lookup"><span data-stu-id="978c8-123">If an element contains a mix of text and markup, the contents are considered to be mixed content.</span></span> <span data-ttu-id="978c8-124">次に、混合コンテンツを含む要素の例を示します。</span><span class="sxs-lookup"><span data-stu-id="978c8-124">Following is an example of an element with mixed content.</span></span>  
  
```  
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
```  
  
 \</dir>  
  
## <a name="see-also"></a><span data-ttu-id="978c8-125">参照</span><span class="sxs-lookup"><span data-stu-id="978c8-125">See Also</span></span>  
 [<span data-ttu-id="978c8-126">XML エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="978c8-126">XML Editor &#40;SQL Server Management Studio&#41;</span></span>](../ssms/sql-server-management-studio-ssms.md)  
