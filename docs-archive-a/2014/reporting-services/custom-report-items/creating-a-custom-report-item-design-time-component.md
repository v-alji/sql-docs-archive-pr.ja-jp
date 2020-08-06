---
title: カスタム レポート アイテムのデザイン時コンポーネントの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b663dc3b0a9c54d1674bf153ee09dd36e0de7a00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631664"
---
# <a name="creating-a-custom-report-item-design-time-component"></a><span data-ttu-id="765ea-102">カスタム レポート アイテムのデザイン時コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="765ea-102">Creating a Custom Report Item Design-Time Component</span></span>
  <span data-ttu-id="765ea-103">カスタム レポート アイテムのデザイン時コンポーネントは、Visual Studio レポート デザイナー環境で使用できるコントロールです。</span><span class="sxs-lookup"><span data-stu-id="765ea-103">A custom report item design-time component is a control that can be used in the Visual Studio Report Designer environment.</span></span> <span data-ttu-id="765ea-104">カスタム レポート アイテムのデザイン時コンポーネントは、ドラッグ アンド ドロップ操作を使用できるアクティブ化されたデザイン画面、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロパティ ブラウザーとの統合、およびカスタム プロパティ エディター機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="765ea-104">The custom report item design-time component provides an activated design surface that can accept drag-and-drop operations, integration with the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser, and the ability to provide custom property editors.</span></span>  
  
 <span data-ttu-id="765ea-105">カスタム レポート アイテムのデザイン時コンポーネントを使用すると、ユーザーは、デザイン環境のレポート上にカスタム レポート アイテムを配置し、カスタム レポート アイテムのカスタム データ プロパティを設定してから、カスタム レポート アイテムをレポート プロジェクトの一部として保存できます。</span><span class="sxs-lookup"><span data-stu-id="765ea-105">With a custom report item design-time component, the user can position a custom report item on a report in the design environment, set custom data properties on the custom report item, and then save the custom report item as part of the report project.</span></span>  
  
 <span data-ttu-id="765ea-106">開発環境でデザイン時コンポーネントを使用して設定されるプロパティは、ホスト デザイン環境によってシリアル化およびシリアル化解除され、レポート定義言語 (RDL) ファイルに要素として格納されます。</span><span class="sxs-lookup"><span data-stu-id="765ea-106">The properties that are set using the design-time component in the development environment are serialized and deserialized by the host design environment and then stored as elements in the Report Definition Language (RDL) file.</span></span> <span data-ttu-id="765ea-107">レポート プロセッサによるレポートの実行時には、デザイン時コンポーネントを使用して設定されたプロパティが、レポート プロセッサによってカスタム レポート アイテムの実行時コンポーネントに渡されます。実行時コンポーネントは、カスタム レポート アイテムを表示してレポート プロセッサに返します。</span><span class="sxs-lookup"><span data-stu-id="765ea-107">When the report is executed by the report processor, the properties that are set using the design-time component are passed by the report processor to a custom report item run-time component, which renders the custom report item and passes it back to the report processor.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="765ea-108">カスタム レポート アイテムのデザイン時コンポーネントは、[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] コンポーネントとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="765ea-108">The custom report item design-time component is implemented as a [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] component.</span></span> <span data-ttu-id="765ea-109">ここでは、カスタム レポート アイテムのデザイン時コンポーネントに固有の実装詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="765ea-109">This document will describe implementation details specific to the custom report item design-time component.</span></span> <span data-ttu-id="765ea-110">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] を使用したコンポーネント開発の詳細については、MSDN ライブラリの「[Visual Studio のコンポーネント](https://go.microsoft.com/fwlink/?LinkId=116576)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="765ea-110">For more information about developing components using the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], see [Components in Visual Studio](https://go.microsoft.com/fwlink/?LinkId=116576) in the MSDN library.</span></span>  
  
 <span data-ttu-id="765ea-111">完全に実装されたカスタム レポート アイテムの例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services の製品サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="765ea-111">For a sample of a fully implemented custom report item, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="implementing-a-design-time-component"></a><span data-ttu-id="765ea-112">デザイン時コンポーネントの実装</span><span class="sxs-lookup"><span data-stu-id="765ea-112">Implementing a Design-Time Component</span></span>  
 <span data-ttu-id="765ea-113">カスタム レポート アイテムのデザイン時コンポーネントのメイン クラスは、`Microsoft.ReportDesigner.CustomReportItemDesigner` クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="765ea-113">The main class of a custom report item design-time component is inherited from the `Microsoft.ReportDesigner.CustomReportItemDesigner` class.</span></span> <span data-ttu-id="765ea-114">コンポーネント クラスには、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] コントロールで使用される標準の属性に加えて、`CustomReportItem` 属性を定義してください。</span><span class="sxs-lookup"><span data-stu-id="765ea-114">In addition to the standard attributes used for a [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] control, your component class should define a `CustomReportItem` attribute.</span></span> <span data-ttu-id="765ea-115">この属性は、reportserver.config ファイルに定義されたカスタム レポート アイテム名と同じにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="765ea-115">This attribute must correspond to the name of the custom report item as it is defined in the reportserver.config file.</span></span> <span data-ttu-id="765ea-116">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 属性の完全な一覧については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントの「属性」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="765ea-116">For a list of [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] attributes, see Attributes in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="765ea-117">次のコード例では、カスタム レポート アイテムのデザイン時コントロールに属性が適用されています。</span><span class="sxs-lookup"><span data-stu-id="765ea-117">The following code example shows attributes being applied to a custom report item design-time control:</span></span>  
  
```csharp  
namespace PolygonsCRI  
{  
    [LocalizedName("Polygons")]  
    [Editor(typeof(CustomEditor), typeof(ComponentEditor))]  
        [ToolboxBitmap(typeof(PolygonsDesigner),"Polygons.ico")]  
        [CustomReportItem("Polygons")]  
  
    public class PolygonsDesigner : CustomReportItemDesigner  
    {  
...  
```  
  
### <a name="initializing-the-component"></a><span data-ttu-id="765ea-118">コンポーネントの初期化</span><span class="sxs-lookup"><span data-stu-id="765ea-118">Initializing the Component</span></span>  
 <span data-ttu-id="765ea-119">カスタム レポート アイテム用にユーザーが指定したプロパティは、<xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> クラスを使用して渡されます。</span><span class="sxs-lookup"><span data-stu-id="765ea-119">You pass user-specified properties for a custom report item using a <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class.</span></span> <span data-ttu-id="765ea-120">コンポーネントの <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> クラスから新しいインスタンスを作成して既定値に設定する際には、`CustomReportItemDesigner` クラスの実装で `InitializeNewComponent` メソッドをオーバーライドしてください。</span><span class="sxs-lookup"><span data-stu-id="765ea-120">Your implementation of the `CustomReportItemDesigner` class should override the `InitializeNewComponent` method to create a new instance of your component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class and set it to default values.</span></span>  
  
 <span data-ttu-id="765ea-121">次のコードは、コンポーネントの <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> クラスを初期化する際に、カスタム レポート アイテムのデザイン時コンポーネント クラスで `CustomReportItemDesigner.InitializeNewComponent` メソッドをオーバーライドする例です。</span><span class="sxs-lookup"><span data-stu-id="765ea-121">The following code example shows an example of a custom report item design-time component class overriding the `CustomReportItemDesigner.InitializeNewComponent` method to initialize the component's <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> class:</span></span>  
  
```csharp  
public override void InitializeNewComponent()  
        {  
            CustomData = new CustomData();  
            CustomData.DataRowHierarchy = new DataHierarchy();  
  
            // Shape grouping  
            CustomData.DataRowHierarchy.DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].Group.Name = Name + "_Shape";  
            CustomData.DataRowHierarchy.DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Point grouping  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.Name = Name + "_Point";  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Static column  
            CustomData.DataColumnHierarchy = new DataHierarchy();  
            CustomData.DataColumnHierarchy.DataMembers.Add(new DataMember());  
  
            // Points  
            IList<IList<DataValue>> dataValues = new List<IList<DataValue>>();  
            CustomData.DataRows.Add(dataValues);  
            CustomData.DataRows[0].Add(new List<DataValue>());  
            CustomData.DataRows[0][0].Add(NewDataValue("X", ""));  
            CustomData.DataRows[0][0].Add(NewDataValue("Y", ""));  
        }  
```  
  
### <a name="modifying-component-properties"></a><span data-ttu-id="765ea-122">コンポーネントのプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="765ea-122">Modifying Component Properties</span></span>  
 <span data-ttu-id="765ea-123">`CustomData` プロパティをデザイン環境で変更するには、複数の方法があります。</span><span class="sxs-lookup"><span data-stu-id="765ea-123">You can modify `CustomData` properties in the design environment in several ways.</span></span> <span data-ttu-id="765ea-124">デザイン時コンポーネントによって公開され、<xref:System.ComponentModel.BrowsableAttribute> 属性でマークされたあらゆるプロパティは、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロパティ ブラウザーを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="765ea-124">You can modify any properties that are exposed by the design-time component that are marked with the <xref:System.ComponentModel.BrowsableAttribute> attribute by using the [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] property browser.</span></span> <span data-ttu-id="765ea-125">また、プロパティを変更するには、カスタム レポート アイテムのデザイン画面にアイテムをドラッグする方法や、デザイン環境でコントロールを右クリックし、ショートカット メニューの **[プロパティ]** をクリックしてカスタム プロパティ ウィンドウを表示する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="765ea-125">In addition, you can modify properties by dragging items onto the custom report item's design surface, or by right-clicking the control in the design environment and selecting **Properties** on the shortcut menu to display a custom properties window.</span></span>  
  
 <span data-ttu-id="765ea-126">以下のコード例では、`Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` プロパティに <xref:System.ComponentModel.BrowsableAttribute> 属性が適用されています。</span><span class="sxs-lookup"><span data-stu-id="765ea-126">The following code example shows a `Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData` property that has the <xref:System.ComponentModel.BrowsableAttribute> attribute applied:</span></span>  
  
```csharp  
[Browsable(true), Category("Data")]  
public string DataSetName  
{  
      get  
      {  
         return CustomData.DataSetName;  
      }  
      set  
      {  
         CustomData.DataSetName = value;  
      }  
   }  
  
```  
  
 <span data-ttu-id="765ea-127">デザイン時コンポーネントに、カスタム プロパティ エディター ダイアログ ボックスを挿入できます。</span><span class="sxs-lookup"><span data-stu-id="765ea-127">You can provide your design-time component with a custom properties editor dialog box.</span></span> <span data-ttu-id="765ea-128">カスタム プロパティ エディターの実装では、<xref:System.ComponentModel.ComponentEditor> クラスを継承し、プロパティ編集用ダイアログ ボックスのインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="765ea-128">The custom property editor implementation should inherit from the <xref:System.ComponentModel.ComponentEditor> class, and it should create an instance of a dialog box that can be used for property editing.</span></span>  
  
 <span data-ttu-id="765ea-129">次の例は、<xref:System.ComponentModel.ComponentEditor> を継承し、カスタム プロパティ エディター ダイアログ ボックスを表示するクラスの実装です。</span><span class="sxs-lookup"><span data-stu-id="765ea-129">The following example shows an implementation of a class that inherits from <xref:System.ComponentModel.ComponentEditor> and displays a custom property editor dialog box:</span></span>  
  
```csharp  
internal sealed class CustomEditor : ComponentEditor  
{  
   public override bool EditComponent(  
      ITypeDescriptorContext context, object component)  
    {  
     PolygonsDesigner designer = (PolygonsDesigner)component;  
     PolygonProperties dialog = new PolygonProperties();  
     dialog.m_designerComponent = designer;  
     DialogResult result = dialog.ShowDialog();  
     if (result == DialogResult.OK)  
     {  
        designer.Invalidate();  
        designer.ChangeService().OnComponentChanged(designer, null, null, null);  
        return true;  
     }  
     else  
        return false;  
    }  
}  
```  
  
 <span data-ttu-id="765ea-130">カスタム プロパティ エディター ダイアログ ボックスで、レポート デザイナーの式エディターを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="765ea-130">Your custom property editor dialog box can invoke the Report Designer Expression Editor.</span></span> <span data-ttu-id="765ea-131">次の例では、コンボ ボックスの最初の要素をユーザーが選択すると、式エディターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="765ea-131">In the following example, the Expression Editor is invoked when the user selects the first element in the combo box:</span></span>  
  
```csharp  
private void EditableCombo_SelectedIndexChanged(object sender,   
    EventArgs e)  
{  
   ComboBox combo = (ComboBox)sender;  
   if (combo.SelectedIndex == 0 && m_launchEditor)  
   {  
      m_launchEditor = false;  
      ExpressionEditor editor = new ExpressionEditor();  
      string newValue;  
      newValue = (string)editor.EditValue(null, m_designerComponent.Site, m_oldComboValue);  
      combo.Items[0] = newValue;  
   }  
}  
  
```  
  
### <a name="using-designer-verbs"></a><span data-ttu-id="765ea-132">デザイナー動詞の使用</span><span class="sxs-lookup"><span data-stu-id="765ea-132">Using Designer Verbs</span></span>  
 <span data-ttu-id="765ea-133">デザイナー動詞は、イベント ハンドラーにリンクされたメニュー コマンドです。</span><span class="sxs-lookup"><span data-stu-id="765ea-133">A designer verb is a menu command linked to an event handler.</span></span> <span data-ttu-id="765ea-134">デザイナー動詞を追加して、カスタム レポート アイテムの実行時コントロールのデザイン環境での使用時に、コンポーネントのショートカット メニューに表示できます。</span><span class="sxs-lookup"><span data-stu-id="765ea-134">You can add designer verbs that will appear in a component's shortcut menu when your custom report item run-time control is being used in the design environment.</span></span> <span data-ttu-id="765ea-135">実行時コンポーネントで `Verbs` プロパティを使用すると、使用可能なデザイナー動詞の一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="765ea-135">You can return the list of available designer verbs from your run-time component by using the `Verbs` property.</span></span>  
  
 <span data-ttu-id="765ea-136">次のコード例では、デザイナー動詞とイベント ハンドラーが <xref:System.ComponentModel.Design.DesignerVerbCollection> に追加されています。イベント ハンドラー コードも示します。</span><span class="sxs-lookup"><span data-stu-id="765ea-136">The following code example shows a designer verb and an event handler being added to the <xref:System.ComponentModel.Design.DesignerVerbCollection>, as well as the event handler code:</span></span>  
  
```csharp  
public override DesignerVerbCollection Verbs  
{  
    get  
    {  
        if (m_verbs == null)  
        {  
            m_verbs = new DesignerVerbCollection();  
            m_verbs.Add(new DesignerVerb("Proportional Scaling", new EventHandler(OnProportionalScaling)));  
         m_verbs[0].Checked = (GetCustomProperty("poly:Proportional") == bool.TrueString);  
        }  
  
        return m_verbs;  
    }  
}  
  
private void OnProportionalScaling(object sender, EventArgs e)  
{  
   bool proportional = !  
        (GetCustomProperty("poly:Proportional") == bool.TrueString);  
   m_verbs[0].Checked = proportional;  
   SetCustomProperty("poly:Proportional", proportional.ToString());  
   ChangeService().OnComponentChanged(this, null, null, null);  
   Invalidate();  
}  
```  
  
### <a name="using-adornments"></a><span data-ttu-id="765ea-137">装飾の使用</span><span class="sxs-lookup"><span data-stu-id="765ea-137">Using Adornments</span></span>  
 <span data-ttu-id="765ea-138">カスタム レポート アイテム クラスには、`Microsoft.ReportDesigner.Design.Adornment` クラスを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="765ea-138">Custom report item classes can also implement a `Microsoft.ReportDesigner.Design.Adornment` class.</span></span> <span data-ttu-id="765ea-139">装飾を使用すると、カスタム レポート アイテムのコントロールで、デザイン画面のメインの四角形の外に領域を作成できます。</span><span class="sxs-lookup"><span data-stu-id="765ea-139">An adornment allows the custom report item control to provide areas outside the main rectangle of the design surface.</span></span> <span data-ttu-id="765ea-140">これらの領域では、マウス クリックやドラッグ アンド ドロップ操作などのユーザー インターフェイス イベントを扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="765ea-140">These areas can handle user interface events, such as mouse clicks and drag-and-drop operations.</span></span> <span data-ttu-id="765ea-141">`Adornment`名前空間で定義されているクラス [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` は、 <xref:System.Windows.Forms.Design.Behavior.Adorner> Windows フォームで見つかったクラスのパススルー実装です。</span><span class="sxs-lookup"><span data-stu-id="765ea-141">The `Adornment` class that is defined in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] `Microsoft.ReportDesigner` namespace is a pass-through implementation of the <xref:System.Windows.Forms.Design.Behavior.Adorner> class found in Windows Forms.</span></span> <span data-ttu-id="765ea-142">クラスの完全なドキュメントについ `Adorner` ては、MSDN ライブラリの「[動作サービスの概要](https://go.microsoft.com/fwlink/?LinkId=116673)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="765ea-142">For complete documentation on the `Adorner` class, see [Behavior Service Overview](https://go.microsoft.com/fwlink/?LinkId=116673) in the MSDN library.</span></span> <span data-ttu-id="765ea-143">クラスを実装するサンプルコードについ `Microsoft.ReportDesigner.Design.Adornment` ては、「 [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="765ea-143">For sample code that implements a `Microsoft.ReportDesigner.Design.Adornment` class, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
 <span data-ttu-id="765ea-144">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] での Windows フォームを使ったプログラミングの詳細については、MSDN ライブラリの次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="765ea-144">For more information about programming and using Windows Forms in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], see these topics in the MSDN Library:</span></span>  
  
-   <span data-ttu-id="765ea-145">コンポーネントのデザイン時属性</span><span class="sxs-lookup"><span data-stu-id="765ea-145">Design-Time Attributes for Components</span></span>  
  
-   <span data-ttu-id="765ea-146">[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="765ea-146">Components in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span></span>  
  
-   <span data-ttu-id="765ea-147">チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="765ea-147">Walkthrough: Creating a Windows Forms Control that Takes Advantage of Visual Studio Design-Time Features</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="765ea-148">参照</span><span class="sxs-lookup"><span data-stu-id="765ea-148">See Also</span></span>  
 <span data-ttu-id="765ea-149">[カスタムレポートアイテムのアーキテクチャ](custom-report-item-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="765ea-149">[Custom Report Item Architecture](custom-report-item-architecture.md) </span></span>  
 <span data-ttu-id="765ea-150">[カスタムレポートアイテムの実行時コンポーネントの作成](creating-a-custom-report-item-run-time-component.md) </span><span class="sxs-lookup"><span data-stu-id="765ea-150">[Creating a Custom Report Item Run-Time Component](creating-a-custom-report-item-run-time-component.md) </span></span>  
 <span data-ttu-id="765ea-151">[カスタムレポートアイテムクラスライブラリ](custom-report-item-class-libraries.md) </span><span class="sxs-lookup"><span data-stu-id="765ea-151">[Custom Report Item Class Libraries](custom-report-item-class-libraries.md) </span></span>  
 [<span data-ttu-id="765ea-152">方法: カスタム レポート アイテムを配置する</span><span class="sxs-lookup"><span data-stu-id="765ea-152">How to: Deploy a Custom Report Item</span></span>](how-to-deploy-a-custom-report-item.md)  
  
  
