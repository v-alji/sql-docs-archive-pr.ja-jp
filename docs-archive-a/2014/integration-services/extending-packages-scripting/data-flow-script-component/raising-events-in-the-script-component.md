---
title: スクリプト コンポーネントでのイベントの発生 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], raising events
ms.assetid: bb389073-e1d0-4794-8d29-c8b293b6a5e3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78eb44239f4e58e43bdd65c41d5fdeb58d053a6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642168"
---
# <a name="raising-events-in-the-script-component"></a><span data-ttu-id="de3e7-102">スクリプト コンポーネントでのイベントの発生</span><span class="sxs-lookup"><span data-stu-id="de3e7-102">Raising Events in the Script Component</span></span>
  <span data-ttu-id="de3e7-103">イベントは、エラーや警告、タスクの進行状況や状態などのその他の情報を、親パッケージにレポートする方法を提供するものです。</span><span class="sxs-lookup"><span data-stu-id="de3e7-103">Events provide a way to report errors, warnings, and other information, such as task progress or status, to the containing package.</span></span> <span data-ttu-id="de3e7-104">パッケージには、イベントの通知機能を管理するためのイベント ハンドラーがあります。</span><span class="sxs-lookup"><span data-stu-id="de3e7-104">The package provides event handlers for managing event notifications.</span></span> <span data-ttu-id="de3e7-105">スクリプト コンポーネントは、`ScriptMain` クラスの <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> プロパティに対してメソッドを呼び出して、イベントを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="de3e7-105">The Script component can raise events by calling methods on the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property of the `ScriptMain` class.</span></span> <span data-ttu-id="de3e7-106">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージのイベントの処理の詳細については、「[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../../integration-services-ssis-event-handlers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de3e7-106">For more information about how [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] packages handle events, see [Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md).</span></span>  
  
 <span data-ttu-id="de3e7-107">イベントは、パッケージ内で有効な任意のログ プロバイダーに記録できます。</span><span class="sxs-lookup"><span data-stu-id="de3e7-107">Events can be logged to any log provider that is enabled in the package.</span></span> <span data-ttu-id="de3e7-108">ログ プロバイダーは、イベントに関する情報をデータ ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-108">Log providers store information about events in a data store.</span></span> <span data-ttu-id="de3e7-109">スクリプト コンポーネントは、イベントを発生させずに <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドを使用して、情報をログ プロバイダーに記録することもできます。</span><span class="sxs-lookup"><span data-stu-id="de3e7-109">The Script component can also use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method to log information to a log provider without raising an event.</span></span> <span data-ttu-id="de3e7-110"><xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> メソッドの使用方法の詳細については、次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de3e7-110">For more information about how to use the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.Log%2A> method, see the following section.</span></span>  
  
 <span data-ttu-id="de3e7-111">イベントを発生させるには、スクリプト コンポーネントは <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> プロパティによって公開される、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> インターフェイスの次のメソッドのいずれかを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-111">To raise an event, the Script task calls one of the following methods of the <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> interface exposed by the <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.ComponentMetaData%2A> property:</span></span>  
  
|<span data-ttu-id="de3e7-112">Event</span><span class="sxs-lookup"><span data-stu-id="de3e7-112">Event</span></span>|<span data-ttu-id="de3e7-113">説明</span><span class="sxs-lookup"><span data-stu-id="de3e7-113">Description</span></span>|  
|-----------|-----------------|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireCustomEvent%2A>|<span data-ttu-id="de3e7-114">パッケージ内でユーザー定義のカスタム イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="de3e7-114">Raises a user-defined custom event in the package.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireError%2A>|<span data-ttu-id="de3e7-115">パッケージにエラー条件を通知します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-115">Informs the package of an error condition.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireInformation%2A>|<span data-ttu-id="de3e7-116">ユーザーに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-116">Provides information to the user.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireProgress%2A>|<span data-ttu-id="de3e7-117">コンポーネントの進行状況をパッケージに通知します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-117">Informs the package of the progress of the component.</span></span>|  
|<xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.FireWarning%2A>|<span data-ttu-id="de3e7-118">エラー条件ではないが、コンポーネントがユーザーに通知する必要がある状態であることをパッケージに通知します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-118">Informs the package that the component is in a state that warrants user notification, but is not an error condition.</span></span>|  
  
 <span data-ttu-id="de3e7-119">エラー イベントを発生させる簡単な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-119">Here is a simple example of raising an Error event:</span></span>  
  
 `Dim myMetadata as IDTSComponentMetaData100`  
  
 `myMetaData = Me.ComponentMetaData`  
  
 `myMetaData.FireError(...)`  
  
<span data-ttu-id="de3e7-120">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="de3e7-120">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="de3e7-121">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="de3e7-121">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="de3e7-122">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="de3e7-122">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="de3e7-123">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="de3e7-123">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de3e7-124">参照</span><span class="sxs-lookup"><span data-stu-id="de3e7-124">See Also</span></span>  
 <span data-ttu-id="de3e7-125">[Integration Services &#40;SSIS&#41; のイベント ハンドラー](../../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="de3e7-125">[Integration Services &#40;SSIS&#41; Event Handlers](../../integration-services-ssis-event-handlers.md) </span></span>  
 [<span data-ttu-id="de3e7-126">パッケージにイベント ハンドラーを追加する</span><span class="sxs-lookup"><span data-stu-id="de3e7-126">Add an Event Handler to a Package</span></span>](../../add-an-event-handler-to-a-package.md)  
  
  
