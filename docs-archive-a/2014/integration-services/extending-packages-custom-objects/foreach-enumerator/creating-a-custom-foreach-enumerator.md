---
title: カスタム Foreach 列挙子の作成 | Microsoft Docs
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
- custom foreach enumerators [Integration Services], creating
ms.assetid: 050e8455-2ed0-4b6d-b3ea-4e80e6c28487
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d99970d466aa53d25a80f0600f1fce7819e94956
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633910"
---
# <a name="creating-a-custom-foreach-enumerator"></a><span data-ttu-id="41e27-102">カスタム Foreach 列挙子の作成</span><span class="sxs-lookup"><span data-stu-id="41e27-102">Creating a Custom Foreach Enumerator</span></span>
  <span data-ttu-id="41e27-103">カスタム foreach 列挙子の作成手順は、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の他のカスタム オブジェクトの作成手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="41e27-103">The steps involved in creating a custom foreach enumerator are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="41e27-104">基本クラスを継承する新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="41e27-104">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="41e27-105">foreach 列挙子用の基本クラスは <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> です。</span><span class="sxs-lookup"><span data-stu-id="41e27-105">For a foreach enumerator, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator>.</span></span>  
  
-   <span data-ttu-id="41e27-106">クラスに、オブジェクトの種類を識別する属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="41e27-106">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="41e27-107">foreach 列挙子用の属性は <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> です。</span><span class="sxs-lookup"><span data-stu-id="41e27-107">For a foreach enumerator, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute>.</span></span>  
  
-   <span data-ttu-id="41e27-108">基本クラスのメソッドとプロパティの実装をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="41e27-108">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="41e27-109">foreach 列挙子で、最も重要なのは、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> メソッドです。</span><span class="sxs-lookup"><span data-stu-id="41e27-109">For a foreach enumerator, the most important is the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method.</span></span>  
  
-   <span data-ttu-id="41e27-110">必要に応じて、カスタム ユーザー インターフェイスを開発します。</span><span class="sxs-lookup"><span data-stu-id="41e27-110">Optionally, develop a custom user interface.</span></span> <span data-ttu-id="41e27-111">その場合、foreach 列挙子では、<xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> インターフェイスを実装するクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="41e27-111">For a foreach enumerator, this requires a class that implements the <xref:Microsoft.SqlServer.Dts.Runtime.IDTSForEachEnumeratorUI> interface.</span></span>  
  
 <span data-ttu-id="41e27-112">カスタム列挙子は、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> コンテナーによってホストされます。</span><span class="sxs-lookup"><span data-stu-id="41e27-112">A custom enumerator is hosted by the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container.</span></span> <span data-ttu-id="41e27-113">実行時は、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> コンテナーが、カスタム列挙子の <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="41e27-113">At run time, the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> container calls the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator.GetEnumerator%2A> method of the custom enumerator.</span></span> <span data-ttu-id="41e27-114">カスタム列挙子は、`IEnumerable` などの `ArrayList` インターフェイスを実装するオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="41e27-114">The custom enumerator returns an object that implements the `IEnumerable` interface, such as an `ArrayList`.</span></span> <span data-ttu-id="41e27-115">次に、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> はコレクション内の各要素を繰り返し処理し、ユーザー定義変数を介して現在の要素の値を制御フローに渡し、コンテナーの制御フローを実行します。</span><span class="sxs-lookup"><span data-stu-id="41e27-115">The <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> then iterates over each element in the collection, provides the value of the current element to the control flow through a user-defined variable, and executes the control flow in the container.</span></span>  
  
## <a name="getting-started-with-a-custom-foreach-enumerator"></a><span data-ttu-id="41e27-116">カスタム ForEach 列挙子の概要</span><span class="sxs-lookup"><span data-stu-id="41e27-116">Getting Started with a Custom ForEach Enumerator</span></span>  
  
### <a name="creating-projects-and-classes"></a><span data-ttu-id="41e27-117">プロジェクトおよびクラスの作成</span><span class="sxs-lookup"><span data-stu-id="41e27-117">Creating Projects and Classes</span></span>  
 <span data-ttu-id="41e27-118">すべてのマネージド foreach 列挙子は <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> 基本クラスから派生するため、カスタム foreach 列挙子を作成するには、最初に任意のマネージド プログラミング言語でクラス ライブラリ プロジェクトを作成し、基本クラスを継承するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="41e27-118">Because all managed foreach enumerators derive from the <xref:Microsoft.SqlServer.Dts.Runtime.ForEachEnumerator> base class, the first step when you create a custom foreach enumerator is to create a class library project in your preferred managed programming language and create a class that inherits from the base class.</span></span> <span data-ttu-id="41e27-119">この派生クラスで、基本クラスのメソッドとプロパティをオーバーライドして、カスタム機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="41e27-119">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>  
  
 <span data-ttu-id="41e27-120">同じソリューション内に、もう 1 つのクラス ライブラリ プロジェクトをカスタム ユーザー インターフェイス用に作成します。</span><span class="sxs-lookup"><span data-stu-id="41e27-120">In the same solution, create a second class library project for the custom user interface.</span></span> <span data-ttu-id="41e27-121">配置を容易にするため、ユーザー インターフェイス用に別個のアセンブリを使用することをお勧めします。そうすれば、foreach 列挙子やそのユーザー インターフェイスの更新や再配置を個別に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="41e27-121">A separate assembly for the user interface is recommended for ease of deployment because it allows you to update and redeploy the foreach enumerator or its user interface independently.</span></span>  
  
 <span data-ttu-id="41e27-122">どちらのプロジェクトも、アセンブリに署名するよう構成します。アセンブリは、厳密な名前のキー ファイルを使用して、ビルド時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="41e27-122">Configure both projects to sign the assemblies that will be generated at build time by using a strong name key file.</span></span>  
  
### <a name="applying-the-dtsforeachenumerator-attribute"></a><span data-ttu-id="41e27-123">DtsForEachEnumerator 属性の適用</span><span class="sxs-lookup"><span data-stu-id="41e27-123">Applying the DtsForEachEnumerator Attribute</span></span>  
 <span data-ttu-id="41e27-124">作成したクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> 属性を適用して、そのクラスが foreach 列挙子として識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="41e27-124">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute> attribute to the class that you have created to identify it as a foreach enumerator.</span></span> <span data-ttu-id="41e27-125">この属性は、foreach 列挙子の名前や説明など、デザイン時の情報を表します。</span><span class="sxs-lookup"><span data-stu-id="41e27-125">This attribute provides design-time information such as the name and description of the foreach enumerator.</span></span> <span data-ttu-id="41e27-126">プロパティは、[ `Name` **Foreach ループエディター** ] ダイアログボックスの [**コレクション**] タブにある使用可能な列挙子のドロップダウンリストに表示されます。</span><span class="sxs-lookup"><span data-stu-id="41e27-126">The `Name` property appears in the dropdown list of available enumerators on the **Collection** tab of the **Foreach Loop Editor** dialog box.</span></span>  
  
 <span data-ttu-id="41e27-127"><xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> プロパティを使用して、foreach 列挙子をそのカスタム ユーザー インターフェイスにリンクします。</span><span class="sxs-lookup"><span data-stu-id="41e27-127">Use the <xref:Microsoft.SqlServer.Dts.Runtime.DtsForEachEnumeratorAttribute.UITypeName%2A> property to link the foreach enumerator to its custom user interface.</span></span> <span data-ttu-id="41e27-128">このプロパティに必要な公開キー トークンを取得するには、**sn.exe -t** を使用して、ユーザー インターフェイス アセンブリへの署名に使用するキー ペア (.snk) ファイルから公開キー トークンを表示します。</span><span class="sxs-lookup"><span data-stu-id="41e27-128">To obtain the public key token that is required for this property, you an use **sn.exe -t** to display the public key token from the key pair (.snk) file that you intend to use to sign the user interface assembly.</span></span>  
  
```vb  
Imports System  
Imports Microsoft.SqlServer.Dts.Runtime  
Namespace Microsoft.Samples.SqlServer.Dts  
    <DtsForEachEnumerator(DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")> _   
    Public Class MyEnumerator  
     Inherits ForEachEnumerator  
        'Insert code here.  
    End Class  
End Namespace  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
namespace Microsoft.Samples.SqlServer.Dts  
{  
    [DtsForEachEnumerator( DisplayName = "MyEnumerator", Description="A sample custom enumerator", UITypeName="FullyQualifiedTypeName,AssemblyName,Version=1.00.000.00,Culture=Neutral,PublicKeyToken=<publickeytoken>")]  
    public class MyEnumerator : ForEachEnumerator  
    {  
        //Insert code here.  
    }  
}  
```  
  
## <a name="building-deploying-and-debugging-a-custom-enumerator"></a><span data-ttu-id="41e27-129">カスタム列挙子の作成、配置、およびデバッグ</span><span class="sxs-lookup"><span data-stu-id="41e27-129">Building, Deploying, and Debugging a Custom Enumerator</span></span>  
 <span data-ttu-id="41e27-130">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] でカスタム foreach 列挙子を作成、配置、およびデバッグする手順は、他の種類のカスタム オブジェクトで必要な手順とほとんど同様です。</span><span class="sxs-lookup"><span data-stu-id="41e27-130">The steps for building, deploying, and debugging a custom foreach enumerator in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="41e27-131">詳細については、「[カスタム オブジェクトのビルド、配置、デバッグ](../building-deploying-and-debugging-custom-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41e27-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>  
  
<span data-ttu-id="41e27-132">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="41e27-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="41e27-133">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="41e27-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="41e27-134">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="41e27-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="41e27-135">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="41e27-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e27-136">参照</span><span class="sxs-lookup"><span data-stu-id="41e27-136">See Also</span></span>  
 <span data-ttu-id="41e27-137">[カスタム Foreach 列挙子のコーディング](coding-a-custom-foreach-enumerator.md) </span><span class="sxs-lookup"><span data-stu-id="41e27-137">[Coding a Custom Foreach Enumerator](coding-a-custom-foreach-enumerator.md) </span></span>  
 [<span data-ttu-id="41e27-138">カスタム ForEach 列挙子用ユーザー インターフェイスの開発</span><span class="sxs-lookup"><span data-stu-id="41e27-138">Developing a User Interface for a Custom ForEach Enumerator</span></span>](developing-a-user-interface-for-a-custom-foreach-enumerator.md)  
  
  
