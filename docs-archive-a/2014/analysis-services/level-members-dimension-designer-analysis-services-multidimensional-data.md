---
title: レベルとメンバー ([ブラウザー] タブ、ディメンションデザイナー) (Analysis Services 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21680f00b82b5410e2c7a67122fdcfeb78c999dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743585"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a>レベルとメンバー ([ブラウザー] タブ、ディメンション デザイナー) (Analysis Services - 多次元データ)
  このペインを使用すると、現在選択している階層と言語のメンバーを参照できます。 参照する階層または言語を選択するには、 **ツール バー** ペインの **[階層]** および **[言語]** オプションを使用します。 ツールバーペインの詳細については、「[ツールバー &#40;ブラウザータブ」、「ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)」を参照してください。  
  
## <a name="writeback-mode"></a>書き戻しモード  
 書き戻しモードが有効な場合、このペインの機能は変わります。 書き戻しモードを有効にするには、選択したディメンションを書き込み可能にする (つまり、ディメンションの `WriteEnabled` プロパティを true に設定する) 必要があり、さらにディメンションを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに配置する必要があります。  
  
 書き戻しモードを有効にするには、 **ツールバー** ペインで **[書き戻し]** を選択するか、 **レベルとメンバー** ペインを右クリックしてショートカット メニューから **[書き戻し]** を選択します。  
  
 書き戻しモードを有効にした場合、 **レベルとメンバー** ペインで次の操作を実行できるようになります。  
  
|To Do|実行内容|  
|-----------|-------------|  
|選択した階層に兄弟メンバーと子メンバーを作成する。|選択したメンバーを右クリックしてショートカット メニューを開き、兄弟メンバーを作成する場合は **[兄弟の作成]**、子メンバーを作成する場合は **[子の作成]** を選択します。|  
|階層の中で選択したメンバーを上または下に移動する。|選択したメンバーを適切な親メンバーまたは子メンバーにドラッグするか、 **ツール バー** ペインの **[インデント]** または **[インデント解除]** をクリックして、選択したメンバーの階層のレベルを上または下に移動します。|  
|選択したメンバーの名前を変更する。|選択したメンバーを右クリックして **[名前の変更]** を選択するか、選択したメンバーをクリックします。|  
|メンバーのプロパティの値を編集する。|選択したメンバーの選択したメンバー プロパティの値をダブルクリックして、値を編集します。|  
  
## <a name="options"></a>Options  
 **[現在のレベル]**  
 **[ツリー]** で現在選択されているメンバーが属するレベルが表示されます。  
  
 **ツリー**  
 現在選択されている階層と言語のメンバーが表示されます。  
  
 ツール バー ペインの **[メンバーのプロパティ]** オプションでメンバーのプロパティを選択した場合、各メンバーのプロパティが列として表示されます。  
  
 書き戻しモードが有効な場合、ディメンション内のキー属性に関連付けられている各キー列について、1 つの列が表示されます。  
  
## <a name="context-menu"></a>コンテキスト メニュー  
 選択したメンバーの **レベルとメンバー** ペインの任意の場所を右クリックして表示されるショートカット メニューでは、次のオプションを使用できます。  
  
 **[兄弟の作成]**  
 選択したメンバーと同じレベルに、新しいメンバーを作成します。  
  
> [!NOTE]  
>  このオプションは、[(すべて)] レベル以外のレベルのメンバーが選択されている場合にのみ有効になります。  
  
> [!NOTE]  
>  このオプションは、書き戻しモードが有効な場合にのみ表示されます。  
  
 **[子の作成]**  
 選択したメンバーより 1 つ下のレベルに、選択したメンバーの子として新しいメンバーを作成します。  
  
> [!NOTE]  
>  このオプションは、最も低いレベル以外のメンバーが選択されている場合にのみ有効になります。  
  
> [!NOTE]  
>  このオプションは、書き戻しモードが有効な場合にのみ表示されます。  
  
 **［切り取り］**  
 選択したメンバーをクリップボードにコピーした後、階層から削除します。  
  
> [!NOTE]  
>  このオプションは、[すべて] メンバー以外のメンバーが選択されている場合にのみ有効になります。  
  
> [!NOTE]  
>  このオプションは、書き戻しモードが有効な場合にのみ表示されます。  
  
 **貼り付け**  
 選択したメンバーの直後に、以前に **[切り取り]** を使用して切り取ったメンバーを貼り付けます。  
  
> [!NOTE]  
>  このオプションは、書き戻しモードが有効な場合にのみ表示されます。  
  
 **削除**  
 選択されているメンバーを階層から削除します。  
  
> [!NOTE]  
>  このオプションは、[すべて] メンバー以外のメンバーが選択されている場合にのみ有効になります。  
  
> [!NOTE]  
>  このオプションは、書き戻しモードが有効な場合にのみ表示されます。  
  
 **Rename**  
 選択したメンバーの名前を編集する場合に選択します。  
  
> [!NOTE]  
>  このオプションは、[すべて] メンバー以外のメンバーが選択されている場合にのみ有効になります。  
  
> [!NOTE]  
>  このオプションは、書き戻しモードが有効な場合にのみ表示されます。  
  
 **[メンバーのフィルター選択]**  
 **[メンバーのフィルター選択]** ダイアログ ボックスを表示し、**レベルとメンバー**に表示される選択した階層のメンバーをフィルター選択できます。 **[メンバーのフィルター選択]** ダイアログ ボックスの詳細については、「[[メンバーのフィルター選択] ダイアログ ボックス &#40;Analysis Services - 多次元データ&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。  
  
 **すべて展開**  
 **[ツリー]** 内のすべてのメンバーを展開します。  
  
> [!NOTE]  
>  このオプションは、最も低いレベル以外のメンバーが選択されている場合にのみ有効になります。  
  
 **すべて折りたたむ**  
 **[ツリー]** 内のすべてのメンバーを折りたたみます。  
  
 **[メンバーの展開]**  
 **[ツリー]** 内で選択されているメンバーを展開します。  
  
 **[メンバーの折りたたみ]**  
 **[ツリー]** 内で選択されているメンバーを折りたたみます。  
  
 **[書き戻し]**  
 選択すると、書き戻しモードを有効にします。  
  
## <a name="see-also"></a>参照  
 [ツールバー &#40;[ブラウザー] タブ、ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)   
 [ブラウザー &#40;ディメンションデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  