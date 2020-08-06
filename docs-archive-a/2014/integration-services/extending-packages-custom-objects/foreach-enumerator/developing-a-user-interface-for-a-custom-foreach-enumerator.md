---
title: カスタム ForEach 列挙子用ユーザー インターフェイスの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom foreach enumerators
- custom foreach enumerators [Integration Services], developing custom user interface
ms.assetid: 8aa4aa80-c9ba-42b3-ba87-ae5ea5d3cac3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 500c67f1ee4577190d7a24286bbfeed0347e92fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641167"
---
# <a name="developing-a-user-interface-for-a-custom-foreach-enumerator"></a><span data-ttu-id="d237c-102">カスタム ForEach 列挙子用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="d237c-102">Developing a User Interface for a Custom ForEach Enumerator</span></span>
  <span data-ttu-id="d237c-103">基本クラスのプロパティとメソッドをオーバーライドしてカスタム機能を実装したら、Foreach 列挙子用のカスタム ユーザー インターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d237c-103">After you have overridden the implementation of the properties and methods of the base class to provide your custom functionality, you may want to create a custom user interface for your Foreach enumerator.</span></span> <span data-ttu-id="d237c-104">カスタム ユーザー インターフェイスを作成しない場合、ユーザーは [プロパティ] ウィンドウを使用して新しいカスタム Foreach 列挙子を構成することしかできません。</span><span class="sxs-lookup"><span data-stu-id="d237c-104">If you do not create a custom user interface, users can only configure the new custom Foreach enumerator by using the Properties window.</span></span>  
  
 <span data-ttu-id="d237c-105">カスタム ユーザー インターフェイスのプロジェクトまたはアセンブリで、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI> を実装するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="d237c-105">In a custom user interface project or assembly, you create a class that implements <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI>.</span></span> <span data-ttu-id="d237c-106">このクラスは、通常他の Windows フォーム コントロールをホストするための複合コントロールの作成に使用される System.Windows.Forms.UserControl から派生します。</span><span class="sxs-lookup"><span data-stu-id="d237c-106">This class derives from System.Windows.Forms.UserControl, which is typically used to create a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="d237c-107">作成するコントロールは、**[Foreach ループ エディター]** の **[コレクション]** タブの **[列挙子の構成]** 領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="d237c-107">The control that you create is displayed in the **Enumerator configuration** area of the **Collection** tab of the **Foreach Loop Editor**.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d237c-108">「[Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md)」(カスタム オブジェクトのビルド、配置、およびデバッグ) で説明されているようにカスタム ユーザー インターフェイスに署名してビルドし、グローバル アセンブリ キャッシュにインストールしたら、このクラスの完全修飾名を <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> の <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> プロパティで忘れずに指定してください。</span><span class="sxs-lookup"><span data-stu-id="d237c-108">After signing and building your custom user interface and installing it in the global assembly cache as described in [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md), remember to provide the fully qualified name of this class in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
## <a name="coding-the-user-interface-control-class"></a><span data-ttu-id="d237c-109">ユーザー インターフェイス コントロール クラスのコーディング</span><span class="sxs-lookup"><span data-stu-id="d237c-109">Coding the User Interface Control Class</span></span>  
  
### <a name="initializing-the-user-interface"></a><span data-ttu-id="d237c-110">ユーザー インターフェイスの初期化</span><span class="sxs-lookup"><span data-stu-id="d237c-110">Initializing the User Interface</span></span>  
 <span data-ttu-id="d237c-111"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> メソッドをオーバーライドして、ホスト オブジェクトへの参照、接続マネージャーのコレクションへの参照、およびパッケージで定義された変数をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="d237c-111">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.Initialize%2A> method to cache references to the host object, and to the collections of connection managers and variables defined in the package.</span></span>  
  
### <a name="setting-properties-on-the-user-interface-control"></a><span data-ttu-id="d237c-112">ユーザー インターフェイス コントロールでのプロパティの設定</span><span class="sxs-lookup"><span data-stu-id="d237c-112">Setting Properties on the User Interface Control</span></span>  
 <span data-ttu-id="d237c-113">ユーザー インターフェイス クラスの派生元である UserControl クラスは、他の Windows フォーム コントロールをホストするための複合コントロールとして使用することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="d237c-113">The UserControl class, from which the user interface class is derived, is intended for use as a composite control to host other Windows Forms controls.</span></span> <span data-ttu-id="d237c-114">このクラスが他のコントロールをホストするため、コントロールをドラッグ アンド ドロップし、それらを並べ替え、プロパティを設定し、すべての Windows フォーム アプリケーションと同じようにコントロールのイベントに実行時に応答することにより、カスタム ユーザー インターフェイスをデザインできます。</span><span class="sxs-lookup"><span data-stu-id="d237c-114">Because this class hosts other controls, you can design your custom user interface by dragging and dropping controls, arranging them, setting their properties, and responding at run time to their events as in any Windows Forms application.</span></span>  
  
### <a name="saving-settings"></a><span data-ttu-id="d237c-115">設定の保存</span><span class="sxs-lookup"><span data-stu-id="d237c-115">Saving Settings</span></span>  
 <span data-ttu-id="d237c-116"><xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> メソッドをオーバーライドして、ユーザーがエディターを終了したときに、ユーザーが選択した値をコントロールから列挙子のプロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d237c-116">You override the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumeratorUI.SaveSettings%2A> method to copy the values selected by the user from the controls to the properties of the enumerator when the user closes the editor.</span></span>  
  
<span data-ttu-id="d237c-117">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="d237c-117">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d237c-118">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d237c-118">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d237c-119">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="d237c-119">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d237c-120">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="d237c-120">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d237c-121">参照</span><span class="sxs-lookup"><span data-stu-id="d237c-121">See Also</span></span>  
 <span data-ttu-id="d237c-122">[カスタム Foreach 列挙子の作成](creating-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="d237c-122">[Creating a Custom Foreach Enumerator](creating-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="d237c-123">カスタム Foreach 列挙子のコーディング</span><span class="sxs-lookup"><span data-stu-id="d237c-123">Coding a Custom Foreach Enumerator</span></span>](coding-a-custom-foreach-enumerator.md)  
  
  
