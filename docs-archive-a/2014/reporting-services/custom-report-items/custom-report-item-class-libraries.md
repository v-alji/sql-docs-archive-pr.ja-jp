---
title: カスタム レポート アイテムのクラス ライブラリ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 60f8cf912eb6ff3f5080e9cf757df40f37e65079
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631662"
---
# <a name="custom-report-item-class-libraries"></a><span data-ttu-id="60b3e-102">カスタム レポート アイテムのクラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="60b3e-102">Custom Report Item Class Libraries</span></span>
  <span data-ttu-id="60b3e-103">カスタム レポート アイテムは、`Microsoft.ReportDesigner` 名前空間のクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-103">Custom report items use classes from the `Microsoft.ReportDesigner` namespace.</span></span> <span data-ttu-id="60b3e-104">カスタム レポート アイテムを実装する際に使用するクラスは、2 つの主なカテゴリに分類できます。1 つは、カスタム レポート アイテム インフラストラクチャをサポートするためにデザインされた独自のクラス、もう 1 つは、関連するレポート定義言語 (RDL) 要素の機能をカプセル化するマネージド ラッパー クラスです。</span><span class="sxs-lookup"><span data-stu-id="60b3e-104">The classes used to implement a custom report item can be grouped into two main categories: unique classes designed to support custom report item infrastructure, and managed wrapper classes that encapsulate the functionality of relevant Report Definition Language (RDL) elements.</span></span> <span data-ttu-id="60b3e-105">これらのクラスの使用方法のコード サンプルについては、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services の製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60b3e-105">For a code sample on how to use these classes, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="custom-report-item-infrastructure-classes"></a><span data-ttu-id="60b3e-106">カスタム レポート アイテム インフラストラクチャのクラス</span><span class="sxs-lookup"><span data-stu-id="60b3e-106">Custom Report Item Infrastructure Classes</span></span>  
 <span data-ttu-id="60b3e-107">以下のクラスは、カスタム レポート アイテムを実装するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-107">The following classes are used to implement a custom report item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60b3e-108">以下の各表はすべてを網羅したものではなく、各クラスの最も一般的に使用されるプロパティやメソッドのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="60b3e-108">The following tables are not complete listings; they include only the most commonly used properties and methods for each class.</span></span>  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a><span data-ttu-id="60b3e-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span><span class="sxs-lookup"><span data-stu-id="60b3e-109">Microsoft.ReportDesigner.CustomReportItemDesigner</span></span>  
 <span data-ttu-id="60b3e-110">カスタム レポート アイテムのメイン クラスです。</span><span class="sxs-lookup"><span data-stu-id="60b3e-110">This is the main custom report item class.</span></span> <span data-ttu-id="60b3e-111">カスタム レポート アイテムの実装のメイン クラスは、このクラスを継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60b3e-111">The main class of your custom report item implementation must inherit from this class.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="60b3e-112">パブリック プロパティ</span><span class="sxs-lookup"><span data-stu-id="60b3e-112">Public Properties</span></span>  
  
|||  
|-|-|  
|`Name`|<span data-ttu-id="60b3e-113">カスタム レポート アイテムの名前</span><span class="sxs-lookup"><span data-stu-id="60b3e-113">The name of the custom report item.</span></span>|  
|`Type`|<span data-ttu-id="60b3e-114">カスタム レポート アイテムの種類。</span><span class="sxs-lookup"><span data-stu-id="60b3e-114">The type of the custom report item.</span></span>|  
|`CustomData`|<span data-ttu-id="60b3e-115">デザイン時に指定されたカスタム レポート アイテムのデータ プロパティをカプセル化する <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> オブジェクト</span><span class="sxs-lookup"><span data-stu-id="60b3e-115">A <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> object that encapsulates the custom report item data properties specified at design time.</span></span>|  
|`CustomProperties`|<span data-ttu-id="60b3e-116">カスタム レポート アイテムのカスタム プロパティのコレクション</span><span class="sxs-lookup"><span data-stu-id="60b3e-116">A collection of custom properties for the custom report item.</span></span>|  
|`Height`|<span data-ttu-id="60b3e-117">カスタム レポート アイテム コントロールの高さ</span><span class="sxs-lookup"><span data-stu-id="60b3e-117">The height of the custom report item control.</span></span>|  
|`Width`|<span data-ttu-id="60b3e-118">カスタム レポート アイテム コントロールの幅</span><span class="sxs-lookup"><span data-stu-id="60b3e-118">The width of the custom report item control.</span></span>|  
|`Report`|<span data-ttu-id="60b3e-119">レポート レベルのプロパティ (レポートのデータセットの一覧など) のコンテナー</span><span class="sxs-lookup"><span data-stu-id="60b3e-119">A container for the report-level properties, such as the list of datasets in the report.</span></span>|  
|`AltReportItem`|<span data-ttu-id="60b3e-120">カスタム レポート アイテムの実行時コントロールがサポートされていない場合に使用される代替レポート アイテム オブジェクト</span><span class="sxs-lookup"><span data-stu-id="60b3e-120">The alternate report item object, to be used where the custom report item run-time control is not supported.</span></span>|  
|`Style`|<span data-ttu-id="60b3e-121">カスタム レポート アイテムのスタイルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="60b3e-121">The style properties for the custom report item.</span></span>|  
|`Adornment`|<span data-ttu-id="60b3e-122">コントロールのインタラクティブな編集のために使用される装飾ウィンドウ</span><span class="sxs-lookup"><span data-stu-id="60b3e-122">An adornment window used for interactive editing of the control.</span></span>|  
|`Site`|<span data-ttu-id="60b3e-123">コンポーネントの `ISite` です。</span><span class="sxs-lookup"><span data-stu-id="60b3e-123">The `ISite` of the component.</span></span>|  
|`DesignerVerbCollection`|<span data-ttu-id="60b3e-124">コントロールのショートカット メニューのカスタム動詞の配列</span><span class="sxs-lookup"><span data-stu-id="60b3e-124">An array of custom verbs for the control's shortcut menu.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="60b3e-125">パブリック メソッド</span><span class="sxs-lookup"><span data-stu-id="60b3e-125">Public Methods</span></span>  
  
|||  
|-|-|  
|`BeginEdit`|<span data-ttu-id="60b3e-126">コントロールのインタラクティブな編集をアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="60b3e-126">Activates interactive editing for the control.</span></span>|  
|`DoDefaultAction`|<span data-ttu-id="60b3e-127">コントロールをダブルクリックしたとき、またはコントロールに対して Enter キーを押したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-127">Called in response to double-clicking or pressing Return on the control.</span></span>|  
|`EndEdit`|<span data-ttu-id="60b3e-128">コントロールのインタラクティブな編集を非アクティブにします。</span><span class="sxs-lookup"><span data-stu-id="60b3e-128">Deactivates interactive editing for the control.</span></span>|  
|`GetService`|<span data-ttu-id="60b3e-129">サービスを表すオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-129">Returns an object which represents a service.</span></span>|  
|`InitializeNewComponent`|<span data-ttu-id="60b3e-130">新しいカスタム レポート アイテムの作成時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-130">Called when a new custom report item is created.</span></span>|  
|`Invalidate`|<span data-ttu-id="60b3e-131">コントロールの表面全体を再描画します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-131">Repaints the entire surface of the control.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragDrop`|<span data-ttu-id="60b3e-132">オブジェクトをコントロールにドラッグすると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-132">Called when an object is dragged onto the control.</span></span>|  
|`OnPaint`|<span data-ttu-id="60b3e-133">`Paint` イベントに応答して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-133">Called in response to the `Paint` event.</span></span>|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a><span data-ttu-id="60b3e-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span><span class="sxs-lookup"><span data-stu-id="60b3e-134">Microsoft.ReportDesigner.CustomReportItemAttribute</span></span>  
 <span data-ttu-id="60b3e-135">この属性は、カスタム レポート アイテムの種類を識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-135">This is the attribute used to identify the type of the custom report item.</span></span> <span data-ttu-id="60b3e-136">名前は `Name` レポートデザイナー構成ファイル内の要素の <> 属性の値と一致する必要があり `ReportItem` ます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-136">The name must match the value of the <`Name`> attribute of the `ReportItem` element in the Report Designer configuration file.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="60b3e-137">パブリック メソッド</span><span class="sxs-lookup"><span data-stu-id="60b3e-137">Public Methods</span></span>  
  
|||  
|-|-|  
|`CustomReportItemAttribute`|<span data-ttu-id="60b3e-138">CustomReportItemAttribute オブジェクトを構築します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-138">Constructs the CustomReportItemAttribute object.</span></span>|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a><span data-ttu-id="60b3e-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span><span class="sxs-lookup"><span data-stu-id="60b3e-139">Microsoft.ReportDesigner.LocalizedNameAttribute</span></span>  
 <span data-ttu-id="60b3e-140">この属性は、カスタム レポート アイテム デザイナーで使用する表示名を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-140">This is the attribute used to specify display name to use for the custom report item designer.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="60b3e-141">パブリック メソッド</span><span class="sxs-lookup"><span data-stu-id="60b3e-141">Public Methods</span></span>  
  
|||  
|-|-|  
|`LocalizedNameAttribute`|<span data-ttu-id="60b3e-142">LocalizedNameAttribute オブジェクトを構築します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-142">Constructs the LocalizedNameAttribute object.</span></span>|  
  
### <a name="microsoftreportdesigneradornment"></a><span data-ttu-id="60b3e-143">Microsoft.ReportDesigner.Adornment</span><span class="sxs-lookup"><span data-stu-id="60b3e-143">Microsoft.ReportDesigner.Adornment</span></span>  
 <span data-ttu-id="60b3e-144">`Adornment` クラスは、カスタム レポート アイテムのデザイン時コンポーネントによって、デザイン画面のメインの四角形の外に領域を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-144">The `Adornment` class is used by the custom report item design-time component to provide areas outside of the main rectangle of the design surface.</span></span> <span data-ttu-id="60b3e-145">これらの領域では、マウス クリックやドラッグ アンド ドロップ操作などのユーザー インターフェイス イベントを扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-145">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="60b3e-146">パブリック メソッド</span><span class="sxs-lookup"><span data-stu-id="60b3e-146">Public Methods</span></span>  
  
|||  
|-|-|  
|`OnShow`|<span data-ttu-id="60b3e-147">`Adornment` がアクティブになると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-147">Called when the `Adornment` is activated.</span></span>|  
|`OnHide`|<span data-ttu-id="60b3e-148">`Adornment` が非アクティブになると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-148">Called when the `Adornment` is deactivated.</span></span>|  
|`Paint`|<span data-ttu-id="60b3e-149">`Paint` イベントに応答して呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-149">Called in response to the `Paint` event.</span></span>|  
|`OnDragEnter`<br /><br /> `OnDragOver`<br /><br /> `OnDragLeave`<br /><br /> `OnDragDrop`|<span data-ttu-id="60b3e-150">オブジェクトを `Adornment` にドラッグすると呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-150">Called when an object is dragged into the `Adornment`.</span></span>|  
  
### <a name="microsoftreportdesigneradornerservice"></a><span data-ttu-id="60b3e-151">Microsoft.ReportDesigner.AdornerService</span><span class="sxs-lookup"><span data-stu-id="60b3e-151">Microsoft.ReportDesigner.AdornerService</span></span>  
 <span data-ttu-id="60b3e-152">このクラスは、カスタム レポート アイテムのデザイン時コンポーネントの `Adornment` オブジェクトをサポートするためにカスタム レポート アイテムによって使用される、表示サービスのコレクションを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-152">This class is used to provide a collection of display services used by the custom report item to support `Adornment` objects for the custom report item design-time component.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="60b3e-153">パブリック プロパティ</span><span class="sxs-lookup"><span data-stu-id="60b3e-153">Public Properties</span></span>  
  
|||  
|-|-|  
|`AdornerWindowBounds`|<span data-ttu-id="60b3e-154">Adorner ウィンドウの境界</span><span class="sxs-lookup"><span data-stu-id="60b3e-154">The bounds of the Adorner window.</span></span>|  
|`AdornerWindowRegion`|<span data-ttu-id="60b3e-155">Adorner ウィンドウの領域</span><span class="sxs-lookup"><span data-stu-id="60b3e-155">The region of the Adorner window.</span></span>|  
|`AdornerWindowGraphics`|<span data-ttu-id="60b3e-156">Adorner ウィンドウのグラフィック コンテキスト</span><span class="sxs-lookup"><span data-stu-id="60b3e-156">A graphics context for the Adorner window.</span></span>|  
  
#### <a name="public-methods"></a><span data-ttu-id="60b3e-157">パブリック メソッド</span><span class="sxs-lookup"><span data-stu-id="60b3e-157">Public Methods</span></span>  
  
|||  
|-|-|  
|`ComponentRectInDesignerFrame`|<span data-ttu-id="60b3e-158">デザイナー フレームの座標に変換されたコンポーネントの境界を返します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-158">Returns the bounds of the component translated into designer frame coordinates.</span></span>|  
|`InvalidateAdorner`|<span data-ttu-id="60b3e-159">Adorner ウィンドウを無効にします。</span><span class="sxs-lookup"><span data-stu-id="60b3e-159">Invalidates the Adorner window.</span></span>|  
|`PointToAdorner`|<span data-ttu-id="60b3e-160">Adorner ウィンドウの座標に変換された画面座標の点を返します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-160">Returns a point in screen coordinates translated to Adorner window coordinates.</span></span>|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a><span data-ttu-id="60b3e-161">Microsoft.ReportDesigner.ExpressionEditor</span><span class="sxs-lookup"><span data-stu-id="60b3e-161">Microsoft.ReportDesigner.ExpressionEditor</span></span>  
 <span data-ttu-id="60b3e-162">このクラスは、カスタム レポート アイテムのデザイン時コントロールから式エディターを呼び出すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-162">This class can be used from your custom report item design-time control to invoke the Expression Editor.</span></span>  
  
#### <a name="public-methods"></a><span data-ttu-id="60b3e-163">パブリック メソッド</span><span class="sxs-lookup"><span data-stu-id="60b3e-163">Public Methods</span></span>  
  
|||  
|-|-|  
|`EditValue`|<span data-ttu-id="60b3e-164">式エディターを呼び出して、渡されたオブジェクト値で初期化します。</span><span class="sxs-lookup"><span data-stu-id="60b3e-164">Invokes the Expression Editor, initialized with the given object value.</span></span>|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a><span data-ttu-id="60b3e-165">Microsoft.ReportDesigner.IFieldsDataObject</span><span class="sxs-lookup"><span data-stu-id="60b3e-165">Microsoft.ReportDesigner.IFieldsDataObject</span></span>  
 <span data-ttu-id="60b3e-166">このクラスは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] フィールドのコレクションであり、デザイン環境でドラッグ アンド ドロップ イベントをサポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-166">This class is a collection of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] fields, and is used to support drag-and-drop events in the design environment.</span></span> <span data-ttu-id="60b3e-167">`IReportItemDataObject` から継承されます。</span><span class="sxs-lookup"><span data-stu-id="60b3e-167">Inherits from `IReportItemDataObject`.</span></span>  
  
#### <a name="public-properties"></a><span data-ttu-id="60b3e-168">パブリック プロパティ</span><span class="sxs-lookup"><span data-stu-id="60b3e-168">Public Properties</span></span>  
  
|||  
|-|-|  
|`DataSetName`|<span data-ttu-id="60b3e-169">ドロップされるフィールドを含むデータセットの名前</span><span class="sxs-lookup"><span data-stu-id="60b3e-169">The name of the dataset containing the fields to be dropped.</span></span>|  
|`Fields`|<span data-ttu-id="60b3e-170">ドロップされるフィールド (`Microsoft.ReportDesigner.Field`) のコレクション</span><span class="sxs-lookup"><span data-stu-id="60b3e-170">The collection of fields (`Microsoft.ReportDesigner.Field`) to be dropped.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60b3e-171">参照</span><span class="sxs-lookup"><span data-stu-id="60b3e-171">See Also</span></span>  
 <span data-ttu-id="60b3e-172">[レポート定義言語 &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="60b3e-172">[Report Definition Language &#40;SSRS&#41;](../reports/report-definition-language-ssrs.md) </span></span>  
 <span data-ttu-id="60b3e-173">[カスタムレポートアイテムの実行時コンポーネントの作成](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="60b3e-173">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 [<span data-ttu-id="60b3e-174">カスタム レポート アイテムのデザイン時コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="60b3e-174">Creating a Custom Report Item Design-Time Component</span></span>](creating-a-custom-report-item-design-time-component.md)  
  
  
