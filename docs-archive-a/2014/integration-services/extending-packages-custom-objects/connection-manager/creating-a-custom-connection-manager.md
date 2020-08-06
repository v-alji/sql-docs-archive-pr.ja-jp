---
title: カスタム接続マネージャーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom connection managers [Integration Services], creating
ms.assetid: e83f8e02-ace4-42e0-b979-2f6be1460985
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 857efebbe311e5510e15cae9e78a2b424559ded7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742414"
---
# <a name="creating-a-custom-connection-manager"></a><span data-ttu-id="2686c-102">カスタム接続マネージャーの作成</span><span class="sxs-lookup"><span data-stu-id="2686c-102">Creating a Custom Connection Manager</span></span>
  <span data-ttu-id="2686c-103">カスタム接続マネージャーを作成するために必要な手順は、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の他のカスタム オブジェクトの作成手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="2686c-103">The steps that you must follow to create a custom connection manager are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="2686c-104">基本クラスを継承する新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2686c-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="2686c-105">接続マネージャー用の基本クラスは <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> です。</span><span class="sxs-lookup"><span data-stu-id="2686c-105">For a connection manager, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase>.</span></span>  
  
-   <span data-ttu-id="2686c-106">クラスに、オブジェクトの種類を識別する属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="2686c-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="2686c-107">接続マネージャー用の属性は <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> です。</span><span class="sxs-lookup"><span data-stu-id="2686c-107">For a connection manager, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute>.</span></span>  
  
-   <span data-ttu-id="2686c-108">基本クラスのメソッドとプロパティの実装をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="2686c-108">Override the implementation of the methods and properties of the base class.</span></span> <span data-ttu-id="2686c-109">接続マネージャーでは、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> プロパティ、<xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> メソッド、および <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> メソッドが対象です。</span><span class="sxs-lookup"><span data-stu-id="2686c-109">For a connection manager, these include the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ReleaseConnection%2A> methods.</span></span>  
  
-   <span data-ttu-id="2686c-110">必要に応じて、カスタム ユーザー インターフェイスを開発します。</span><span class="sxs-lookup"><span data-stu-id="2686c-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="2686c-111">その場合、接続マネージャーでは、<xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> インターフェイスを実装するクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="2686c-111">For a connection manager, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsConnectionManagerUI> interface.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2686c-112">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に組み込まれているタスク、変換元、および変換先の多くは、組み込みの接続マネージャーの特定の種類でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="2686c-112">Most of the tasks, sources, and destinations that have been built into [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] work only with specific types of built-in connection managers.</span></span> <span data-ttu-id="2686c-113">そのため、これらのサンプルは組み込みのタスクおよびコンポーネントではテストできません。</span><span class="sxs-lookup"><span data-stu-id="2686c-113">Therefore, these samples cannot be tested with the built-in tasks and components.</span></span>  
  
## <a name="getting-started-with-a-custom-connection-manager"></a><span data-ttu-id="2686c-114">カスタム接続マネージャーの概要</span><span class="sxs-lookup"><span data-stu-id="2686c-114">Getting Started with a Custom Connection Manager</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="2686c-115">プロジェクトおよびクラスの作成</span><span class="sxs-lookup"><span data-stu-id="2686c-115">Creating Projects and Classes</span></span>  
 <span data-ttu-id="2686c-116">すべてのマネージド接続マネージャーは <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基本クラスから派生するため、カスタム接続マネージャーを作成するには、最初に任意のマネージド プログラミング言語でクラス ライブラリ プロジェクトを作成してから、基本クラスを継承するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2686c-116">Because all managed connection managers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> base class, the first step when you create a custom connection manager is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="2686c-117">この派生クラスで、基本クラスのメソッドとプロパティをオーバーライドして、カスタム機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="2686c-117">In this derived class, you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="2686c-118">同じソリューション内に、もう 1 つのクラス ライブラリ プロジェクトをカスタム ユーザー インターフェイス用に作成します。</span><span class="sxs-lookup"><span data-stu-id="2686c-118">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="2686c-119">配置を容易にするため、ユーザー インターフェイス用に別個のアセンブリを使用することをお勧めします。そうすれば、接続マネージャーやそのユーザー インターフェイスの更新や再配置を個別に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2686c-119">A separate assembly for the user interface is recommended for ease of deployment because it lets you update and redeploy the connection manager or its user interface independently.</span></span>  
  
 <span data-ttu-id="2686c-120">どちらのプロジェクトも、アセンブリに署名するよう構成します。アセンブリは、厳密な名前のキー ファイルを使用して、ビルド時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="2686c-120">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsconnection-attribute"></a><span data-ttu-id="2686c-121">DtsConnection 属性の適用</span><span class="sxs-lookup"><span data-stu-id="2686c-121">Applying the DtsConnection Attribute</span></span>  
 <span data-ttu-id="2686c-122">作成したクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 属性を適用して、そのクラスが接続マネージャーとして識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="2686c-122">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> attribute to the class that you have created to identify it as a connection manager.</span></span> <span data-ttu-id="2686c-123">この属性には、接続マネージャーの名前、説明、および接続の種類など、デザイン時の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="2686c-123">This attribute provides design-time information such as the name, description, and connection type of the connection manager.</span></span> <span data-ttu-id="2686c-124"><xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A>プロパティと `Description` プロパティは、[ **Type** `Description` **SSIS 接続マネージャーの追加**] ダイアログボックスに表示される型と列に対応します。このダイアログボックスは、でパッケージの接続を構成するときに表示され [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2686c-124">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.ConnectionType%2A> and `Description` properties correspond to the **Type** and `Description` columns displayed in the **Add SSIS Connection Manager** dialog box, which is displayed when configuring connections for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="2686c-125"><xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> プロパティを使用して、接続マネージャーをそのカスタム ユーザー インターフェイスにリンクします。</span><span class="sxs-lookup"><span data-stu-id="2686c-125">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute.UITypeName%2A> property to link the connection manager to its custom user interface.</span></span> <span data-ttu-id="2686c-126">このプロパティに必要な公開キー トークンを取得するには、**sn.exe -t** を使用して、ユーザー インターフェイス アセンブリへの署名に使用するキー ペア (.snk) ファイルから公開キー トークンを表示します。</span><span class="sxs-lookup"><span data-stu-id="2686c-126">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
<DtsConnection(ConnectionType:="SQLVB", _  
  DisplayName:="SqlConnectionManager (VB)", _  
  Description:="Connection manager for Sql Server", _  
  UITypeName:="SqlConnMgrUIVB.SqlConnMgrUIVB,SqlConnMgrUIVB,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")> _  
Public Class SqlConnMgrVB  
  Inherits ConnectionManagerBase  
  . . .  
End Class  
```  
  
```csharp  
[DtsConnection(ConnectionType = "SQLCS",  
  DisplayName = "SqlConnectionManager (CS)",  
  Description = "Connection manager for Sql Server",  
  UITypeName = "SqlConnMgrUICS.SqlConnMgrUICS,SqlConnMgrUICS,Version=1.0.0.0,Culture=neutral,PublicKeyToken=<insert public key token here>")]  
public class SqlConnMgrCS :  
ConnectionManagerBase  
{  
  . . .  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-connection-manager"></a><span data-ttu-id="2686c-127">カスタム接続マネージャーのビルド、配置、およびデバッグ</span><span class="sxs-lookup"><span data-stu-id="2686c-127">Building, Deploying, and Debugging a Custom Connection Manager</span></span>  
 <span data-ttu-id="2686c-128">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のカスタム接続マネージャーをビルド、配置、およびデバッグする手順は、他の種類のカスタム オブジェクトの手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="2686c-128">The steps for building, deploying, and debugging a custom connection manager in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are similar to the steps for other types of custom objects.</span></span> <span data-ttu-id="2686c-129">詳細については、「[カスタム オブジェクトのビルド、配置、デバッグ](../building-deploying-and-debugging-custom-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2686c-129">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="2686c-130">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="2686c-130">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2686c-131">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2686c-131">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2686c-132">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="2686c-132">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2686c-133">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="2686c-133">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2686c-134">参照</span><span class="sxs-lookup"><span data-stu-id="2686c-134">See Also</span></span>  
 <span data-ttu-id="2686c-135">[カスタム接続マネージャーのコーディング](coding-a-custom-connection-manager.md) </span><span class="sxs-lookup"><span data-stu-id="2686c-135">[Coding a Custom Connection Manager](coding-a-custom-connection-manager.md) </span></span>  
 [<span data-ttu-id="2686c-136">カスタム接続マネージャー用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="2686c-136">Developing a User Interface for a Custom Connection Manager</span></span>](developing-a-user-interface-for-a-custom-connection-manager.md)  
  
  
