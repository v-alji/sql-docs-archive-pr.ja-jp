---
title: カスタム タスクの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom tasks [Integration Services], creating
ms.assetid: 42965c09-1782-4cdb-9ce1-216af4c23e0a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f752acad7a442a8e0aad2d24e94938c14195a35d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642183"
---
# <a name="creating-a-custom-task"></a><span data-ttu-id="21e22-102">カスタム タスクの作成</span><span class="sxs-lookup"><span data-stu-id="21e22-102">Creating a Custom Task</span></span>
  <span data-ttu-id="21e22-103">カスタム タスクの作成手順は、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の他のカスタム オブジェクトの作成手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="21e22-103">The steps involved in creating a custom task are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="21e22-104">基本クラスを継承する新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21e22-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="21e22-105">タスクの場合、基本クラスは [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) です。</span><span class="sxs-lookup"><span data-stu-id="21e22-105">For a task, the base class is [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task).</span></span>  
  
-   <span data-ttu-id="21e22-106">クラスに、オブジェクトの種類を識別する属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="21e22-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="21e22-107">タスクの属性は <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> です。</span><span class="sxs-lookup"><span data-stu-id="21e22-107">For a task, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute>.</span></span>  
  
-   <span data-ttu-id="21e22-108">基本クラスのメソッドとプロパティの実装をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="21e22-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="21e22-109">タスクでは、<xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> メソッドおよび <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> メソッドが対象です。</span><span class="sxs-lookup"><span data-stu-id="21e22-109">For a task, these include the <xref:Microsoft.SqlServer.Dts.Runtime.Task.Validate%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.Task.Execute%2A> methods.</span></span>  
  
-   <span data-ttu-id="21e22-110">必要に応じて、カスタム ユーザー インターフェイスを開発します。</span><span class="sxs-lookup"><span data-stu-id="21e22-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="21e22-111">タスクでは、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> インターフェイスを実装するクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="21e22-111">For a task, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsTaskUI> interface.</span></span>  
  
## <a name="getting-started-with-a-custom-task"></a><span data-ttu-id="21e22-112">カスタム タスクの概要</span><span class="sxs-lookup"><span data-stu-id="21e22-112">Getting Started with a Custom Task</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="21e22-113">プロジェクトおよびクラスの作成</span><span class="sxs-lookup"><span data-stu-id="21e22-113">Creating Projects and Classes</span></span>  
 <span data-ttu-id="21e22-114">すべてのマネージド タスクは [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) 基本クラスから派生するため、カスタム タスクを作成するには、最初に任意のマネージド プログラミング言語でクラス ライブラリ プロジェクトを作成し、基本クラスを継承するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="21e22-114">Because all managed tasks derive from the [Microsoft.SqlServer.Dts.Runtime.Task](/dotnet/api/microsoft.sqlserver.dts.runtime.task) base class, the first step when you create a custom task is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="21e22-115">この派生クラスで、基本クラスのメソッドとプロパティをオーバーライドして、カスタム機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="21e22-115">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="21e22-116">同じソリューション内に、もう 1 つのクラス ライブラリ プロジェクトをカスタム ユーザー インターフェイス用に作成します。</span><span class="sxs-lookup"><span data-stu-id="21e22-116">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="21e22-117">配置を容易にするため、ユーザー インターフェイス用に別個のアセンブリを使用することをお勧めします。そうすれば、接続マネージャーやそのユーザー インターフェイスの更新や再配置を個別に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="21e22-117">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="21e22-118">どちらのプロジェクトも、アセンブリに署名するよう構成します。アセンブリは、厳密な名前のキー ファイルを使用して、ビルド時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="21e22-118">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtstask-attribute"></a><span data-ttu-id="21e22-119">DtsTask 属性の適用</span><span class="sxs-lookup"><span data-stu-id="21e22-119">Applying the DtsTask Attribute</span></span>  
 <span data-ttu-id="21e22-120">作成したクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> 属性を適用して、そのクラスがタスクとして識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="21e22-120">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute> attribute to the class that you have created to identify it as a task.</span></span> <span data-ttu-id="21e22-121">この属性には、名前、説明、およびタスクの種類など、デザイン時の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="21e22-121">This attribute provides design-time information such as the name, description, and task type of the task.</span></span>  
  
 <span data-ttu-id="21e22-122"><xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> プロパティを使用して、タスクをそのカスタム ユーザー インターフェイスにリンクします。</span><span class="sxs-lookup"><span data-stu-id="21e22-122">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsTaskAttribute.UITypeName%2A> property to link the task to its custom user interface.</span></span> <span data-ttu-id="21e22-123">このプロパティに必要な公開キー トークンを取得するには、**sn.exe -t** を使用して、ユーザー インターフェイス アセンブリへの署名に使用するキー ペア (.snk) ファイルから公開キー トークンを表示します。</span><span class="sxs-lookup"><span data-stu-id="21e22-123">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
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
  
## <a name="building-deploying-and-debugging-a-custom-task"></a><span data-ttu-id="21e22-124">カスタム タスクの作成、配置、およびデバッグ</span><span class="sxs-lookup"><span data-stu-id="21e22-124">Building, Deploying, and Debugging a Custom Task</span></span>  
 <span data-ttu-id="21e22-125">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] でカスタム タスクを作成、配置、およびデバッグする手順は、その他の種類のカスタム オブジェクトで必要な手順とほとんど同様です。</span><span class="sxs-lookup"><span data-stu-id="21e22-125">The steps for building, deploying, and debugging a custom task in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="21e22-126">詳細については、「[カスタム オブジェクトのビルド、配置、デバッグ](../building-deploying-and-debugging-custom-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21e22-126">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="21e22-127">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="21e22-127">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="21e22-128">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="21e22-128">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="21e22-129">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="21e22-129">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="21e22-130">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="21e22-130">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e22-131">参照</span><span class="sxs-lookup"><span data-stu-id="21e22-131">See Also</span></span>  
 <span data-ttu-id="21e22-132">[カスタム タスクの作成](creating-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="21e22-132">[Creating a Custom Task](creating-a-custom-task.md) </span></span>  
 <span data-ttu-id="21e22-133">[カスタム タスクのコーディング](coding-a-custom-task.md) </span><span class="sxs-lookup"><span data-stu-id="21e22-133">[Coding a Custom Task](coding-a-custom-task.md) </span></span>  
 [<span data-ttu-id="21e22-134">カスタム タスク用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="21e22-134">Developing a User Interface for a Custom Task</span></span>](developing-a-user-interface-for-a-custom-task.md)  
  
  
