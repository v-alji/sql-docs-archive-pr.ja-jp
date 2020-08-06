---
title: カスタム タスク用ユーザー インターフェイスの開発 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom user interfaces [Integration Services]
- IDtsTaskUI interface
- DtsTaskAttribute attribute
- custom tasks [Integration Services], user interface
- custom user interface [Integration Services], custom tasks
- user interface [Integration Services]
- SSIS custom tasks, user interface
ms.assetid: 1e940cd1-c5f8-4527-b678-e89ba5dc398a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ed96bbc302cba4c207e5ce7b2e4fb4b74fed4ee2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644554"
---
# <a name="developing-a-user-interface-for-a-custom-task"></a><span data-ttu-id="d1052-102">カスタム タスク用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="d1052-102">Developing a User Interface for a Custom Task</span></span>
  <span data-ttu-id="d1052-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のオブジェクト モデルを使用すると、カスタム タスクの開発者は、タスク用のユーザー インターフェイスを容易に作成できます。作成後、このユーザー インターフェイスは [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] に統合して表示することができます。</span><span class="sxs-lookup"><span data-stu-id="d1052-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] object model provides custom task developers the ability to easily create a custom user interface for a task that can then be integrated and displayed in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="d1052-104">このユーザー インターフェイスでは、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーのユーザーに役に立つ情報を提供でき、カスタム タスクのプロパティや設定を正しく構成するための指針とすることができます。</span><span class="sxs-lookup"><span data-stu-id="d1052-104">The user interface can provide helpful information to the user in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, and guide users to correctly configure the properties and settings of the custom task.</span></span>  
  
 <span data-ttu-id="d1052-105">タスク用のカスタム ユーザー インターフェイスを開発するには、2 つの重要なクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1052-105">Developing a custom user interface for a task involves using two important classes.</span></span> <span data-ttu-id="d1052-106">次の表は、これらのクラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="d1052-106">The following table describes those classes.</span></span>  
  
|<span data-ttu-id="d1052-107">クラス</span><span class="sxs-lookup"><span data-stu-id="d1052-107">Class</span></span>|<span data-ttu-id="d1052-108">説明</span><span class="sxs-lookup"><span data-stu-id="d1052-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>|<span data-ttu-id="d1052-109">マネージド タスクを識別する属性。この属性のプロパティによってデザイン時の情報を提供し、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでのオブジェクトの表示方法と操作方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="d1052-109">An attribute that identifies a managed task, and supplies design-time information through its properties to control how [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer displays and interacts with the object.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI>|<span data-ttu-id="d1052-110">タスクとカスタム ユーザー インターフェイスを関連付けるためにタスクが使用するインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="d1052-110">An interface used by the task to associate the task with its custom user interface.</span></span>|  
  
 <span data-ttu-id="d1052-111">このセクションでは、ユーザー インターフェイスを開発する際の <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性および <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> インターフェイスの役割について説明し、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでタスクを作成、統合、配置、デバッグする方法について詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="d1052-111">This section describes the role of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute and the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface when you are developing a user interface for a custom task, and provides details about how to create, integrate, deploy, and debug the task within [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="d1052-112">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーには、タスクのユーザー インターフェイスへの複数のエントリ ポイントがあります。つまり、ショートカット メニューの **[編集]** を選択し、タスクをダブルクリックするか、プロパティ シートの下部にある **[エディターの表示]** リンクをクリックできます。</span><span class="sxs-lookup"><span data-stu-id="d1052-112">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer provides multiple entry points to the user interface for the task: the user can select **Edit** on the shortcut menu, double-click the task, or click the **Show Editor** link at the bottom of the property sheet.</span></span> <span data-ttu-id="d1052-113">これらのエントリ ポイントのいずれかにアクセスすると、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーはタスク用のユーザー インターフェイスが含まれているアセンブリを探して読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d1052-113">When the user accesses one of these entry points, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer locates and loads the assembly that contains the user interface for the task.</span></span> <span data-ttu-id="d1052-114">タスクのユーザー インターフェイスには、[!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] で表示されるプロパティ ダイアログ ボックスを作成する役割があります。</span><span class="sxs-lookup"><span data-stu-id="d1052-114">The user interface for the task is responsible for creating the properties dialog box that is displayed to the user in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="d1052-115">タスクとそのユーザー インターフェイスは個別のエンティティです。</span><span class="sxs-lookup"><span data-stu-id="d1052-115">A task and its user interface are separate entities.</span></span> <span data-ttu-id="d1052-116">ローカライズ、配置、メンテナンスなどの作業を容易にするため、タスクとユーザー インターフェイスは個別のアセンブリに実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1052-116">They should be implemented in separate assemblies to reduce localization, deployment, and maintenance work.</span></span> <span data-ttu-id="d1052-117">タスク DLL は、ユーザー インターフェイスの読み込み、呼び出しを行わず、これには通常、ユーザー インターフェイスに関するいかなる情報も含まれていません。ただし、タスク内でコード化された <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性値に含まれる情報は例外です。</span><span class="sxs-lookup"><span data-stu-id="d1052-117">The task DLL does not load, call, or generally contain any knowledge of its user interface, except for the information that is contained in the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute values coded in the task.</span></span> <span data-ttu-id="d1052-118">タスクとユーザー インターフェイスは、この方法によってのみ関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="d1052-118">This is the only way that a task and its user interface are associated.</span></span>  
  
## <a name="the-dtstask-attribute"></a><span data-ttu-id="d1052-119">DtsTask 属性</span><span class="sxs-lookup"><span data-stu-id="d1052-119">The DtsTask Attribute</span></span>  
 <span data-ttu-id="d1052-120">タスク クラス コードに含まれている <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性により、タスクはユーザー インターフェイスと関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="d1052-120">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute is included in the task class code to associate a task with its user interface.</span></span> <span data-ttu-id="d1052-121">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーでは、タスクをデザイナーに表示する方法を判別するために、属性のプロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1052-121">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the properties of the attribute to determine how to display the task in the designer.</span></span> <span data-ttu-id="d1052-122">これらのプロパティには、表示する名前やアイコン (存在する場合) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1052-122">These properties include the name to display and the icon, if any.</span></span>  
  
 <span data-ttu-id="d1052-123">次の表は、<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性のプロパティを示しています。</span><span class="sxs-lookup"><span data-stu-id="d1052-123">The following table describes the properties of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute.</span></span>  
  
|<span data-ttu-id="d1052-124">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d1052-124">Property</span></span>|<span data-ttu-id="d1052-125">説明</span><span class="sxs-lookup"><span data-stu-id="d1052-125">Description</span></span>|  
|--------------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>|<span data-ttu-id="d1052-126">制御フロー ツールボックスに表示するタスク名。</span><span class="sxs-lookup"><span data-stu-id="d1052-126">Displays the task name in the Control Flow toolbox.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>|<span data-ttu-id="d1052-127">タスクの説明 (<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute> から継承)。</span><span class="sxs-lookup"><span data-stu-id="d1052-127">The task description (inherited from <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute>).</span></span> <span data-ttu-id="d1052-128">ツールヒントに表示されるプロパティです。</span><span class="sxs-lookup"><span data-stu-id="d1052-128">This property is shown in ToolTips.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A>|<span data-ttu-id="d1052-129">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーに表示するアイコン。</span><span class="sxs-lookup"><span data-stu-id="d1052-129">The icon displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.RequiredProductLevel%2A>|<span data-ttu-id="d1052-130">使用する場合は、<xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> 列挙のいずれかの値に設定します。</span><span class="sxs-lookup"><span data-stu-id="d1052-130">If used, set it to one of the values in the <xref:Microsoft.SqlServer.Dts.Runtime.DTSProductLevel> enumeration.</span></span> <span data-ttu-id="d1052-131">たとえば、「 `RequiredProductLevel = DTSProductLevel.None` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="d1052-131">For example, `RequiredProductLevel = DTSProductLevel.None`.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskContact%2A>|<span data-ttu-id="d1052-132">タスクでテクニカル サポートが必要な場合の連絡先に関する情報。</span><span class="sxs-lookup"><span data-stu-id="d1052-132">Holds contact information for occasions when the task requires technical support.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.TaskType%2A>|<span data-ttu-id="d1052-133">タスクに割り当てる型。</span><span class="sxs-lookup"><span data-stu-id="d1052-133">Assigns a type to the task.</span></span>|  
|<span data-ttu-id="d1052-134">Attribute.TypeId</span><span class="sxs-lookup"><span data-stu-id="d1052-134">Attribute.TypeId</span></span>|<span data-ttu-id="d1052-135">派生クラスに実装した場合、この属性の一意の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1052-135">When implemented in a derived class, gets a unique identifier for this Attribute.</span></span> <span data-ttu-id="d1052-136">詳細については、.NET Framework クラス ライブラリの「`Attribute.TypeID` プロパティ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1052-136">For more information, see `Attribute.TypeID` property in the .NET Framework Class Library.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A>|<span data-ttu-id="d1052-137">アセンブリのタイプ名。[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーがアセンブリを読み込むために使用します。</span><span class="sxs-lookup"><span data-stu-id="d1052-137">The type name of the assembly that is used by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to load the assembly.</span></span> <span data-ttu-id="d1052-138">このプロパティは、タスクのユーザー インターフェイス アセンブリを見つけるために使用します。</span><span class="sxs-lookup"><span data-stu-id="d1052-138">This property is used to find the user interface assembly for the task.</span></span>|  
  
 <span data-ttu-id="d1052-139">次のコード例は、<xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> を示します。この例でわかるように、この属性はクラス定義よりも前にコード化されています。</span><span class="sxs-lookup"><span data-stu-id="d1052-139">The following code example shows the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> as it would look, coded above the class definition.</span></span>  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.SSIS.Samples  
{  
  [DtsTask  
  (  
   DisplayName = "MyTask",  
   IconResource = "MyTask.MyTaskIcon.ico",  
   UITypeName = "My Custom Task," +  
   "Version=1.0.0.0," +  
   "Culture = Neutral," +  
   "PublicKeyToken = 12345abc6789de01",  
   TaskType = "PackageMaintenance",  
   TaskContact = "MyTask; company name; any other information",  
   RequiredProductLevel = DTSProductLevel.None  
   )]  
  public class MyTask : Task  
  {  
    // Your code here.  
  }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
  
<DtsTask(DisplayName:="MyTask", _  
 IconResource:="MyTask.MyTaskIcon.ico", _  
 UITypeName:="My Custom Task," & _  
 "Version=1.0.0.0,Culture=Neutral," & _  
 "PublicKeyToken=12345abc6789de01", _  
 TaskType:="PackageMaintenance", _  
 TaskContact:="MyTask; company name; any other information", _  
 RequiredProductLevel:=DTSProductLevel.None)> _  
Public Class MyTask  
  Inherits Task  
  
  ' Your code here.  
  
End Class 'MyTask  
```  
  
 <span data-ttu-id="d1052-140">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーはこの属性の <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> プロパティを参照して、グローバル アセンブリ キャッシュ (GAC) からアセンブリを探し、読み込んでデザイナーで使用します。このプロパティには、アセンブリ名、タイプ名、バージョン、カルチャ、および公開キー トークンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d1052-140">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property of the attribute that includes the assembly name, type name, version, culture, and public key token, to locate the assembly in the Global Assembly Cache (GAC) and load it for use by the designer.</span></span>  
  
 <span data-ttu-id="d1052-141">アセンブリが見つかると、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーは属性内の他のプロパティを使用し、タスクの名前、アイコン、説明など、タスクに関する追加情報を [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーに表示します。</span><span class="sxs-lookup"><span data-stu-id="d1052-141">After the assembly has been located, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer uses the other properties in the attribute to display additional information about the task in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, such as the name, icon, and description of the task.</span></span>  
  
 <span data-ttu-id="d1052-142"><xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>、<xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>、および <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> プロパティは、ユーザーに対してタスクをどのように表示するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1052-142">The <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.DisplayName%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.Localization.DtsLocalizableAttribute.Description%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> properties specify how the task is presented to the user.</span></span> <span data-ttu-id="d1052-143"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> プロパティには、ユーザー インターフェイス アセンブリに埋め込まれたアイコンのリソース ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d1052-143">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.IconResource%2A> property contains the resource ID of the icon embedded in the user interface assembly.</span></span> <span data-ttu-id="d1052-144">デザイナーはこの ID を基にしてアセンブリからアイコン リソースを読み込み、タスクがパッケージに追加されたとき、ツールボックスやデザイナー画面で、タスク名の隣にアイコンを表示します。</span><span class="sxs-lookup"><span data-stu-id="d1052-144">The designer loads the icon resource by ID from the assembly, and displays it next to the task name in the toolbox and on the designer surface when the task is added to a package.</span></span> <span data-ttu-id="d1052-145">タスクがアイコン リソースを提供しない場合、デザイナーはタスク用に既定のアイコンを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1052-145">If a task does not provide an icon resource, the designer uses a default icon for the task.</span></span>  
  
## <a name="the-idtstaskui-interface"></a><span data-ttu-id="d1052-146">IDTSTaskUI インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d1052-146">The IDTSTaskUI Interface</span></span>  
 <span data-ttu-id="d1052-147"><xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> インターフェイスでは、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーが呼び出し、タスクに関連付けられたユーザー インターフェイスを初期化して表示するための、一連のメソッドやプロパティが定義されます。</span><span class="sxs-lookup"><span data-stu-id="d1052-147">The <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface defines the collection of methods and properties called by [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer to initialize and display the user interface associated with the task.</span></span> <span data-ttu-id="d1052-148">タスクのユーザー インターフェイスが起動されると、デザイナーは <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> メソッドを呼び出します。このメソッドは、ユーザーが記述した際にタスク ユーザー インターフェイスに実装されたものです。次に、タスクの <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> コレクション、およびパッケージの <xref:Microsoft.SqlServer.Dts.Runtime.Connections> コレクションを、パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="d1052-148">When the user interface for a task is invoked, the designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.Initialize%2A> method, implemented by the task user interface when you wrote it, and then provides the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collections of the task and package, respectively, as parameters.</span></span> <span data-ttu-id="d1052-149">このコレクションはローカルに保存され、後で <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> メソッド内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1052-149">These collections are stored locally, and used subsequently in the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method.</span></span>  
  
 <span data-ttu-id="d1052-150">デザイナーは <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> メソッドを呼び出して、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで表示するウィンドウを要求します。</span><span class="sxs-lookup"><span data-stu-id="d1052-150">The designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method to request the window that is displayed in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="d1052-151">タスクは、タスクのユーザー インターフェイスを含むウィンドウのインスタンスを作成し、ユーザー インターフェイスをデザイナーに返して表示させます。</span><span class="sxs-lookup"><span data-stu-id="d1052-151">The task creates an instance of the window that contains the user interface for the task, and returns the user interface to the designer for display.</span></span> <span data-ttu-id="d1052-152">通常、オーバーロードされたコンストラクターを介して、<xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> オブジェクトおよび <xref:Microsoft.SqlServer.Dts.Runtime.Connections> オブジェクトがウィンドウに渡されるため、これを使用してタスクを構成できます。</span><span class="sxs-lookup"><span data-stu-id="d1052-152">Typically, the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost> and <xref:Microsoft.SqlServer.Dts.Runtime.Connections> objects are provided to the window through an overloaded constructor so they can be used to configure the task.</span></span>  
  
 <span data-ttu-id="d1052-153">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーはタスク ユーザー インターフェイスの <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> メソッドを呼び出して、タスク用のユーザー インターフェイスを表示します。</span><span class="sxs-lookup"><span data-stu-id="d1052-153">The [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI.GetView%2A> method of the task UI to display the user interface for the task.</span></span> <span data-ttu-id="d1052-154">タスク ユーザー インターフェイスはこのメソッドから Windows フォームを返し、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーは、このフォームをモーダル ダイアログ ボックスとして表示します。</span><span class="sxs-lookup"><span data-stu-id="d1052-154">The task user interface returns the Windows form from this method, and [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer shows this form as a modal dialog box.</span></span> <span data-ttu-id="d1052-155">フォームを閉じると、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーはフォームの `DialogResult` プロパティの値を確認し、タスクが変更されたかどうか、およびその変更を保存する必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d1052-155">When the form is closed, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer examines the value of the `DialogResult` property of the form to determine whether the task has been modified and if these modifications should be saved.</span></span> <span data-ttu-id="d1052-156">`DialogResult` プロパティの値が `OK` の場合、[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーはタスクの持続メソッドを呼び出して変更を保存します。それ以外の場合は、変更は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="d1052-156">If the value of the `DialogResult` property is `OK`, the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer calls the persistence methods of the task to save the changes; otherwise, the changes are discarded.</span></span>  
  
 <span data-ttu-id="d1052-157">次のコード例は、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> インターフェイスを実装します。ここでは、SampleTaskForm という名前の Windows フォーム クラスが存在するものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="d1052-157">The following code sample implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface, and assumes the existence of a Windows form class named SampleTaskForm.</span></span>  
  
```csharp  
using System;  
using System.Windows.Forms;  
using Microsoft.SqlServer.Dts.Runtime;  
using Microsoft.SqlServer.Dts.Runtime.Design;  
  
namespace Sample  
{  
   public class HelloWorldTaskUI : IDtsTaskUI  
   {  
      TaskHost   taskHost;  
      Connections connections;  
      public void Initialize(TaskHost taskHost, IServiceProvider serviceProvider)  
      {  
         this.taskHost = taskHost;  
         IDtsConnectionService cs = serviceProvider.GetService  
         ( typeof( IDtsConnectionService ) ) as   IDtsConnectionService;   
         this.connections = cs.GetConnections();  
      }  
      public ContainerControl GetView()  
      {  
        return new HelloWorldTaskForm(this.taskHost, this.connections);  
      }  
     public void Delete(IWin32Window parentWindow)  
     {  
     }  
     public void New(IWin32Window parentWindow)  
     {  
     }  
   }  
}  
```  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports Microsoft.SqlServer.Dts.Runtime.Design  
Imports System.Windows.Forms  
  
Public Class HelloWorldTaskUI  
  Implements IDtsTaskUI  
  
  Dim taskHost As TaskHost  
  Dim connections As Connections  
  
  Public Sub Initialize(ByVal taskHost As TaskHost, ByVal serviceProvider As IServiceProvider) _  
    Implements IDtsTaskUI.Initialize  
  
    Dim cs As IDtsConnectionService  
  
    Me.taskHost = taskHost  
    cs = DirectCast(serviceProvider.GetService(GetType(IDtsConnectionService)), IDtsConnectionService)  
    Me.connections = cs.GetConnections()  
  
  End Sub  
  
  Public Function GetView() As ContainerControl _  
    Implements IDtsTaskUI.GetView  
  
    Return New HelloWorldTaskForm(Me.taskHost, Me.connections)  
  
  End Function  
  
  Public Sub Delete(ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.Delete  
  
  End Sub  
  
  Public Sub [New](ByVal parentWindow As IWin32Window) _  
    Implements IDtsTaskUI.[New]  
  
  End Sub  
  
End Class  
```  
  
<span data-ttu-id="d1052-158">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="d1052-158">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="d1052-159">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1052-159">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="d1052-160">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="d1052-160">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="d1052-161">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="d1052-161">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1052-162">参照</span><span class="sxs-lookup"><span data-stu-id="d1052-162">See Also</span></span>  
 <span data-ttu-id="d1052-163">[カスタム タスクの作成](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="d1052-163">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="d1052-164">[カスタム タスクのコーディング](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="d1052-164">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="d1052-165">カスタム タスク用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="d1052-165">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
