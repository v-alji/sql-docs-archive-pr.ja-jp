---
title: データ フロー コンポーネントのバージョンのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- PerformUpgrade method
- custom data flow components [Integration Services], upgrading version
- data flow components [Integration Services], upgrading version
- upgrading data flow components [Integration Services]
ms.assetid: c2a298c6-01b3-4ad1-884d-6108165eb56e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f494793a20f1cdcd108553278b82a44daeea75ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645746"
---
# <a name="upgrading-the-version-of-a-data-flow-component"></a><span data-ttu-id="40002-102">データ フロー コンポーネントのバージョンのアップグレード</span><span class="sxs-lookup"><span data-stu-id="40002-102">Upgrading the Version of a Data Flow Component</span></span>
  <span data-ttu-id="40002-103">古いバージョンのコンポーネントで作成されたパッケージには、新しいバージョンのコンポーネントでは使い方が変更されているカスタム プロパティなど、既に有効でないメタデータが含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="40002-103">Packages that were created with an older version of your component may contain metadata that is no longer valid, such as custom properties whose usage has been modified in newer versions of the component.</span></span> <span data-ttu-id="40002-104"><xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> 基本クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> メソッドをオーバーライドすると、以前に古いパッケージに保存したメタデータを、コンポーネントの現在のプロパティを反映して更新することができます。</span><span class="sxs-lookup"><span data-stu-id="40002-104">You can override the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method of the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent> base class to update the metadata previously saved in older packages to reflect the current properties of your component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40002-105">新しいバージョンの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 用にカスタム コンポーネントを再コンパイルする場合、コンポーネントのプロパティが変更されていなければ、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> プロパティの値を変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="40002-105">When you recompile a custom component for a new version of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], you do not have to change the value of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property if the component's properties have not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40002-106">例</span><span class="sxs-lookup"><span data-stu-id="40002-106">Example</span></span>  
 <span data-ttu-id="40002-107">次のサンプルには、架空のデータ フロー コンポーネントのバージョン 2.0 のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="40002-107">The following sample contains code from version 2.0 of a fictitious data flow component.</span></span> <span data-ttu-id="40002-108">新しいバージョン番号は、<xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> の <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute> プロパティで定義されています。</span><span class="sxs-lookup"><span data-stu-id="40002-108">The new version number is defined in the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute.CurrentVersion%2A> property of the <xref:Microsoft.SqlServer.Dts.Pipeline.DtsPipelineComponentAttribute>.</span></span> <span data-ttu-id="40002-109">このコンポーネントには、しきい値を超えた数値の処理方法を定義するプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="40002-109">The component has a property that defines how numeric values that exceed a threshold are to be handled.</span></span> <span data-ttu-id="40002-110">この架空のコンポーネントのバージョン 1.0 では、このプロパティの名前は `RaiseErrorOnInvalidValue` で、指定できる値は true または false のブール値でした。</span><span class="sxs-lookup"><span data-stu-id="40002-110">In version 1.0 of the fictitious component, this property was named `RaiseErrorOnInvalidValue` and accepted a Boolean value of true or false.</span></span> <span data-ttu-id="40002-111">バージョン 2.0 ではプロパティ名が `InvalidValueHandling` に変更されて、カスタム列挙の 4 つの値のいずれかを指定できるようになっています。</span><span class="sxs-lookup"><span data-stu-id="40002-111">In version 2.0 of the fictitious component, the property has been renamed to `InvalidValueHandling` and accepts one of four possible values from a custom enumeration.</span></span>  
  
 <span data-ttu-id="40002-112">次のサンプルのオーバーライドされた <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> メソッドは、以下のアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="40002-112">The overridden <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the following sample performs the following actions:</span></span>  
  
-   <span data-ttu-id="40002-113">コンポーネントの現在のバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="40002-113">Gets the current version of the component.</span></span>  
  
-   <span data-ttu-id="40002-114">古いカスタム プロパティの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="40002-114">Gets the value of the old custom property.</span></span>  
  
-   <span data-ttu-id="40002-115">カスタム プロパティ コレクションから古いプロパティを削除します。</span><span class="sxs-lookup"><span data-stu-id="40002-115">Removes the old property from the custom property collection.</span></span>  
  
-   <span data-ttu-id="40002-116">古いプロパティの値に基づいて新しいカスタム プロパティの値を設定します (可能な場合)。</span><span class="sxs-lookup"><span data-stu-id="40002-116">Sets the value of the new custom property based on the value of the old property, if possible.</span></span>  
  
-   <span data-ttu-id="40002-117">バージョンのメタデータをコンポーネントの現在のバージョンに設定します。</span><span class="sxs-lookup"><span data-stu-id="40002-117">Sets the version metadata to the current version of the component.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="40002-118">データ フロー エンジンは、自身のバージョン番号を <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> メソッドに *pipelineVersion* パラメーターで渡します。</span><span class="sxs-lookup"><span data-stu-id="40002-118">The data flow engine passes its own version number into the <xref:Microsoft.SqlServer.Dts.Pipeline.PipelineComponent.PerformUpgrade%2A> method in the *pipelineVersion* parameter.</span></span> <span data-ttu-id="40002-119">このパラメーターは、バージョン 1.0 の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では有用ではありませんが、今後のバージョンで役に立つようになります。</span><span class="sxs-lookup"><span data-stu-id="40002-119">This parameter is not useful in version 1.0 of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], but may become useful in subsequent versions.</span></span>  
  
 <span data-ttu-id="40002-120">このサンプル コードでは、カスタム プロパティの以前のブール値に直接マップされる 2 つの列挙値のみが使用されています。</span><span class="sxs-lookup"><span data-stu-id="40002-120">The sample code uses only the two enumeration values that map directly to the prior Boolean values for the custom property.</span></span> <span data-ttu-id="40002-121">使用できるその他の列挙値を選択するには、コンポーネントのカスタム ユーザー インターフェイスを使用するか、詳細エディターを使用するか、プログラミングを行います。</span><span class="sxs-lookup"><span data-stu-id="40002-121">Users can select the other available enumeration values through the component's custom user interface, in the Advanced Editor, or programmatically.</span></span> <span data-ttu-id="40002-122">詳細エディターでカスタム プロパティの列挙値を表示する方法については、「[データ フロー コンポーネントのデザイン時のメソッド](design-time-methods-of-a-data-flow-component.md)」の「カスタム プロパティの作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40002-122">For information on displaying enumeration values for a custom property in the Advanced Editor, see "Creating Custom Properties" in [Design-time Methods of a Data Flow Component](design-time-methods-of-a-data-flow-component.md).</span></span>  
  
```vb  
Imports Microsoft.SqlServer.Dts.Pipeline  
Imports Microsoft.SqlServer.Dts.Pipeline.Wrapper  
  
<DtsPipelineComponent(ComponentType:=ComponentType.Transform, CurrentVersion:=2)> _  
Public Class PerformUpgrade  
  Inherits PipelineComponent  
  
  ' Define the set of possible values for the new custom property.  
  Private Enum InvalidValueHandling  
    Ignore  
    FireInformation  
    FireWarning  
    FireError  
  End Enum  
  
  Public Overloads Overrides Sub PerformUpgrade(ByVal pipelineVersion As Integer)  
  
    ' Obtain the current component version from the attribute.  
    Dim componentAttribute As DtsPipelineComponentAttribute = _  
      CType(Attribute.GetCustomAttribute(Me.GetType, _  
      GetType(DtsPipelineComponentAttribute), False), _  
      DtsPipelineComponentAttribute)  
    Dim currentVersion As Integer = componentAttribute.CurrentVersion  
  
    ' If the component version saved in the package is less than  
    '  the current version, Version 2, perform the upgrade.  
    If ComponentMetaData.Version < currentVersion Then  
  
      ' Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
      ' and then remove the property from the custom property collection.  
      Dim oldValue As Boolean = False  
      Try  
        Dim oldProperty As IDTSCustomProperty100 = _  
          ComponentMetaData.CustomPropertyCollection("RaiseErrorOnInvalidValue")  
        oldValue = CType(oldProperty.Value, Boolean)  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue")  
      Catch ex As Exception  
        ' If the old custom property is not available, ignore the error.  
      End Try  
  
      ' Set the value of the new custom property, InvalidValueHandling,  
      '  by using the appropriate enumeration value.  
      Dim newProperty As IDTSCustomProperty100 = _  
        ComponentMetaData.CustomPropertyCollection("InvalidValueHandling")  
      If oldValue = True Then  
        newProperty.Value = InvalidValueHandling.FireError  
      Else  
        newProperty.Value = InvalidValueHandling.Ignore  
      End If  
  
    End If  
  
    ' Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion  
  
  End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Pipeline;  
using Microsoft.SqlServer.Dts.Pipeline.Wrapper;  
  
[DtsPipelineComponent(ComponentType = ComponentType.Transform, CurrentVersion = 2)]  
public class PerformUpgradeCS :  
  PipelineComponent  
  
  // Define the set of possible values for the new custom property.  
{  
  private enum InvalidValueHandling  
  {  
    Ignore,  
    FireInformation,  
    FireWarning,  
    FireError  
  };  
  
  public override void PerformUpgrade(int pipelineVersion)  
  {  
  
    // Obtain the current component version from the attribute.  
    DtsPipelineComponentAttribute componentAttribute =   
      (DtsPipelineComponentAttribute)Attribute.GetCustomAttribute(this.GetType(), typeof(DtsPipelineComponentAttribute), false);  
    int currentVersion = componentAttribute.CurrentVersion;  
  
    // If the component version saved in the package is less than  
    //  the current version, Version 2, perform the upgrade.  
    if (ComponentMetaData.Version < currentVersion)  
  
    // Get the current value of the old custom property, RaiseErrorOnInvalidValue,   
    // and then remove the property from the custom property collection.  
    {  
      bool oldValue = false;  
      try  
      {  
        IDTSCustomProperty100 oldProperty =   
          ComponentMetaData.CustomPropertyCollection["RaiseErrorOnInvalidValue"];  
        oldValue = (bool)oldProperty.Value;  
        ComponentMetaData.CustomPropertyCollection.RemoveObjectByIndex("RaiseErrorOnInvalidValue");  
      }  
      catch (Exception ex)  
      {  
        // If the old custom property is not available, ignore the error.  
      }  
  
      // Set the value of the new custom property, InvalidValueHandling,  
      //  by using the appropriate enumeration value.  
      IDTSCustomProperty100 newProperty =   
         ComponentMetaData.CustomPropertyCollection["InvalidValueHandling"];  
      if (oldValue == true)  
      {  
        newProperty.Value = InvalidValueHandling.FireError;  
      }  
      else  
      {  
        newProperty.Value = InvalidValueHandling.Ignore;  
      }  
  
    }  
  
    // Update the saved component version metadata to the current version.  
    ComponentMetaData.Version = currentVersion;  
  
  }  
  
}  
```  
  
<span data-ttu-id="40002-123">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="40002-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="40002-124">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40002-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="40002-125">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="40002-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="40002-126">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="40002-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
  
