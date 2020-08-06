---
title: カスタム ログ プロバイダーの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom log providers [Integration Services], creating
ms.assetid: fc20af96-9eb8-4195-8d3f-8a4d7c753f24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c1efb736aece2cc8d118c81326989559f0d17a60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716421"
---
# <a name="creating-a-custom-log-provider"></a><span data-ttu-id="e089d-102">カスタム ログ プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="e089d-102">Creating a Custom Log Provider</span></span>
  <span data-ttu-id="e089d-103">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ランタイム環境には広範なログ記録機能があります。</span><span class="sxs-lookup"><span data-stu-id="e089d-103">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time environment has extensive logging capabilities.</span></span> <span data-ttu-id="e089d-104">ログを使用すると、パッケージの実行中に発生するイベントをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="e089d-104">A log lets you capture events that occur during package execution.</span></span> [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="e089d-105">では、さまざまなログ プロバイダーを使用でき、ログを作成して XML、テキスト、データベースなどの形式で保存したり、Windows イベント ログに格納したりできます。</span><span class="sxs-lookup"><span data-stu-id="e089d-105">includes a variety of log providers that enable logs to be created and stored in multiple formats, such as XML, text, database, or in the Windows event log.</span></span> <span data-ttu-id="e089d-106">これらのログ プロバイダーまたは出力形式の中に要件を満たすものがない場合は、カスタム ログ プロバイダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e089d-106">If one of these providers or output formats does not fit your needs, you can create a custom log provider.</span></span>

 <span data-ttu-id="e089d-107">カスタム ログ プロバイダーの作成手順は、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] の他のカスタム オブジェクトの作成手順と同様です。</span><span class="sxs-lookup"><span data-stu-id="e089d-107">The steps involved in creating a custom log provider are similar to the steps for creating any other custom object for [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]:</span></span>

-   <span data-ttu-id="e089d-108">基本クラスを継承する新しいクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e089d-108">Create a new class that inherits from the base class.</span></span> <span data-ttu-id="e089d-109">ログ プロバイダー用の基本クラスは <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> です。</span><span class="sxs-lookup"><span data-stu-id="e089d-109">For a log provider, the base class is <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase>.</span></span>

-   <span data-ttu-id="e089d-110">クラスに、オブジェクトの種類を識別する属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="e089d-110">Apply the attribute that identifies the type of object to the class.</span></span> <span data-ttu-id="e089d-111">ログ プロバイダー用の属性は <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> です。</span><span class="sxs-lookup"><span data-stu-id="e089d-111">For a log provider, the attribute is <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute>.</span></span>

-   <span data-ttu-id="e089d-112">基本クラスのメソッドとプロパティの実装をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e089d-112">Override the implementation of the base class's methods and properties.</span></span> <span data-ttu-id="e089d-113">ログ プロバイダーでは、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> プロパティ、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A> メソッド、<xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A> メソッド、および <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> メソッドが対象です。</span><span class="sxs-lookup"><span data-stu-id="e089d-113">For a log provider, these include the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.ConfigString%2A> property and the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.OpenLog%2A>, <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.Log%2A>, and <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase.CloseLog%2A> methods.</span></span>

-   <span data-ttu-id="e089d-114">カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="e089d-114">Custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

## <a name="getting-started-with-a-custom-log-provider"></a><span data-ttu-id="e089d-115">カスタム ログ プロバイダーの概要</span><span class="sxs-lookup"><span data-stu-id="e089d-115">Getting Started with a Custom Log Provider</span></span>

### <a name="creating-projects-and-classes"></a><span data-ttu-id="e089d-116">プロジェクトおよびクラスの作成</span><span class="sxs-lookup"><span data-stu-id="e089d-116">Creating Projects and Classes</span></span>
 <span data-ttu-id="e089d-117">すべてのマネージド ログ プロバイダーは <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> 基本クラスから派生するため、カスタム ログ プロバイダーを作成するには、最初に任意のマネージド プログラミング言語でクラス ライブラリ プロジェクトを作成し、基本クラスを継承するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e089d-117">Because all managed log providers derive from the <xref:Microsoft.SqlServer.Dts.Runtime.LogProviderBase> base class, the first step when you create a custom log provider is to create a class library project in your preferred managed programming language, and then create a class that inherits from the base class.</span></span> <span data-ttu-id="e089d-118">この派生クラスで、基本クラスのメソッドとプロパティをオーバーライドして、カスタム機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="e089d-118">In this derived class you will override the methods and properties of the base class to implement your custom functionality.</span></span>

 <span data-ttu-id="e089d-119">プロジェクトを構成し、生成するアセンブリを厳密な名前のキー ファイルで署名します。</span><span class="sxs-lookup"><span data-stu-id="e089d-119">Configure the project to sign the assembly that will be generated with a strong name key file.</span></span>

> [!NOTE]
>  <span data-ttu-id="e089d-120">多くの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] ログ プロバイダーには、カスタム ユーザー インターフェイスがあります。カスタム ユーザー インターフェイスには <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> が実装され、**[SSIS ログの構成]** ダイアログ ボックスの **[構成]** ボックスが、使用可能な接続マネージャーがフィルター選択されたドロップダウン リストに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="e089d-120">Many [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] log providers have a custom user interface that implements <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI> and replaces the **Configuration** text box in the **Configure SSIS Logs** dialog box with a filtered dropdown list of available connection managers.</span></span> <span data-ttu-id="e089d-121">ただし、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では実装されていません。</span><span class="sxs-lookup"><span data-stu-id="e089d-121">However custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].</span></span>

### <a name="applying-the-dtslogprovider-attribute"></a><span data-ttu-id="e089d-122">DtsLogProvider 属性の適用</span><span class="sxs-lookup"><span data-stu-id="e089d-122">Applying the DtsLogProvider Attribute</span></span>
 <span data-ttu-id="e089d-123">作成したクラスに <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> 属性を適用して、そのクラスがログ プロバイダーとして識別されるようにします。</span><span class="sxs-lookup"><span data-stu-id="e089d-123">Apply the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> attribute to the class that you have created to identify it as a log provider.</span></span> <span data-ttu-id="e089d-124">この属性には、ログ プロバイダーの名前や説明など、デザイン時の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="e089d-124">This attribute provides design-time information such as the name and description of the log provider.</span></span> <span data-ttu-id="e089d-125">`DisplayName` `Description` 属性のプロパティとプロパティは、 **Name** `Description` 「」でパッケージのログ記録を構成するときに表示される [ **SSIS ログの構成**] エディターに表示される名前と列に対応し [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="e089d-125">The `DisplayName` and `Description` properties of the attribute correspond to the **Name** and `Description` columns displayed in the **Configure SSIS Logs** editor, which is displayed when configuring logging for a package in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="e089d-126">この属性の <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> プロパティは使用されません。</span><span class="sxs-lookup"><span data-stu-id="e089d-126">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.LogProviderType%2A> property of the attribute is not used.</span></span> <span data-ttu-id="e089d-127">ただし、このプロパティには値を入力する必要があります。そうしないと、使用可能なログ プロバイダーの一覧にカスタム ログ プロバイダーが表示されません。</span><span class="sxs-lookup"><span data-stu-id="e089d-127">However, you must enter a value for it, or the custom log provider will not appear in the list of available log providers.</span></span>

> [!NOTE]
>  <span data-ttu-id="e089d-128">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] では、カスタム ログ プロバイダーのカスタム ユーザー インターフェイスは実装されていません。そのため、<xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> の <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> プロパティに値を指定しても、影響がありません。</span><span class="sxs-lookup"><span data-stu-id="e089d-128">Since custom user interfaces for custom log providers are not implemented in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)], specifying a value for the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute.UITypeName%2A> property of the <xref:Microsoft.SqlServer.Dts.Runtime.DtsLogProviderAttribute> has no effect.</span></span>

```vb
<DtsLogProvider(DisplayName:="MyLogProvider", Description:="A simple log provider.", LogProviderType:="Custom")> _
Public Class MyLogProvider
     Inherits LogProviderBase
    ' TODO: Override the base class methods.
End Class
```

```csharp
[DtsLogProvider(DisplayName="MyLogProvider", Description="A simple log provider.", LogProviderType="Custom")]
public class MyLogProvider : LogProviderBase
{
    // TODO: Override the base class methods.
}
```

## <a name="building-deploying-and-debugging-a-custom-log-provider"></a><span data-ttu-id="e089d-129">カスタム ログ プロバイダーの作成、配置、およびデバッグ</span><span class="sxs-lookup"><span data-stu-id="e089d-129">Building, Deploying, and Debugging a Custom Log Provider</span></span>
 <span data-ttu-id="e089d-130">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] でカスタム ログ プロバイダーを作成、配置、およびデバッグする手順は、その他の種類のカスタム オブジェクトで必要な手順とほとんど同様です。</span><span class="sxs-lookup"><span data-stu-id="e089d-130">The steps for building, deploying, and debugging a custom log provider in [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] are very similar to the steps required for other types of custom objects.</span></span> <span data-ttu-id="e089d-131">詳細については、「[カスタム オブジェクトのビルド、配置、デバッグ](../building-deploying-and-debugging-custom-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e089d-131">For more information, see [Building, Deploying, and Debugging Custom Objects](../building-deploying-and-debugging-custom-objects.md).</span></span>

<span data-ttu-id="e089d-132">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="e089d-132">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="e089d-133">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e089d-133">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="e089d-134">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="e089d-134">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="e089d-135">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="e089d-135">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="e089d-136">参照</span><span class="sxs-lookup"><span data-stu-id="e089d-136">See Also</span></span>
 <span data-ttu-id="e089d-137">カスタムログ[プロバイダーのコーディング](coding-a-custom-log-provider.md)カスタム[ログプロバイダーのユーザーインターフェイスを開発](developing-a-user-interface-for-a-custom-log-provider.md)する</span><span class="sxs-lookup"><span data-stu-id="e089d-137">[Coding a Custom Log Provider](coding-a-custom-log-provider.md) [Developing a User Interface for a Custom Log Provider](developing-a-user-interface-for-a-custom-log-provider.md)</span></span>


