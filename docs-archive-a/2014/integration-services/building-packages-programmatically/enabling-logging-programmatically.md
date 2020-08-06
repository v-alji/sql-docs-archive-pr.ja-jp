---
title: プログラムによるログ記録の有効化 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, logs
- SSIS packages, logs
- Integration Services packages, logs
- SSIS logging
- log providers [Integration Services]
- logs [Integration Services], enabling
- LoggingMode property
- LogProvider object
- packages [Integration Services], logs
ms.assetid: 3222a1ed-83eb-421c-b299-a53b67bba740
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ff7f81aca330960e4e94b0343080a37ded8c1273
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715657"
---
# <a name="enabling-logging-programmatically"></a><span data-ttu-id="1db2e-102">プログラムによるログ記録の有効化</span><span class="sxs-lookup"><span data-stu-id="1db2e-102">Enabling Logging Programmatically</span></span>
  <span data-ttu-id="1db2e-103">ランタイム エンジンでは、パッケージの検証中および実行中にイベント固有の情報のキャプチャを有効にするための <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> オブジェクトのコレクションが提供されます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-103">The run-time engine provides a collection of <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects that enable event-specific information to be captured during package validation and execution.</span></span> <span data-ttu-id="1db2e-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> オブジェクトは、<xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> オブジェクト群、つまり <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>、<xref:Microsoft.SqlServer.Dts.Runtime.Package>、<xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>、<xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> などの各オブジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-104"><xref:Microsoft.SqlServer.Dts.Runtime.LogProvider> objects are available to <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer> objects, including the <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>, <xref:Microsoft.SqlServer.Dts.Runtime.Package>, <xref:Microsoft.SqlServer.Dts.Runtime.ForLoop>, and <xref:Microsoft.SqlServer.Dts.Runtime.ForEachLoop> objects.</span></span> <span data-ttu-id="1db2e-105">ログ記録は、個別のコンテナーでも、パッケージ全体でも有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-105">Logging is enabled on individual containers, or on the whole package.</span></span>

 <span data-ttu-id="1db2e-106">コンテナーで使用できるログ プロバイダーには、いくつかの種類があります。</span><span class="sxs-lookup"><span data-stu-id="1db2e-106">There are several types of log providers that are available for a container to use.</span></span> <span data-ttu-id="1db2e-107">そのため、さまざまな形式でログ情報を作成し、保存することができます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-107">This provides the flexibility to create and store log information in many formats.</span></span> <span data-ttu-id="1db2e-108">コンテナー オブジェクトをログ記録に登録するには、まずログ記録を有効にし、次にログ プロバイダーを選択するという、2 段階の処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="1db2e-108">Enlisting a container object in logging is a two-step process: first logging is enabled, and then a log provider is selected.</span></span> <span data-ttu-id="1db2e-109">コンテナーの <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> プロパティおよび <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> プロパティを使用して、ログ記録するイベントを指定し、ログ プロバイダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-109">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingOptions%2A> and <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> properties of the container are used to specify the logged events and to select the log provider.</span></span>

## <a name="enabling-logging"></a><span data-ttu-id="1db2e-110">ログ記録の有効化</span><span class="sxs-lookup"><span data-stu-id="1db2e-110">Enabling Logging</span></span>
 <span data-ttu-id="1db2e-111">ログ記録を実行できる各コンテナーにある <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> プロパティは、コンテナーのイベント情報をイベント ログに記録するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-111">The <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property, found in each container that can perform logging, determines whether the container's event information is recorded to the event log.</span></span> <span data-ttu-id="1db2e-112">このプロパティには <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> 構造の値が割り当てられ、既定でコンテナーの親オブジェクトから継承されます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-112">This property is assigned a value from the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode> structure, and is inherited from the container's parent by default.</span></span> <span data-ttu-id="1db2e-113">コンテナーがパッケージである、つまり親オブジェクトがない場合は、プロパティは <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting> の値を使用します。既定値は `Disabled` です。</span><span class="sxs-lookup"><span data-stu-id="1db2e-113">If the container is a package, and therefore has no parent, the property uses the <xref:Microsoft.SqlServer.Dts.Runtime.DTSLoggingMode.UseParentSetting>, which defaults to `Disabled`.</span></span>

### <a name="selecting-a-log-provider"></a><span data-ttu-id="1db2e-114">ログ プロバイダーの選択</span><span class="sxs-lookup"><span data-stu-id="1db2e-114">Selecting a Log Provider</span></span>
 <span data-ttu-id="1db2e-115"><xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> プロパティを `Enabled` に設定したら、コンテナーの <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> コレクションにログ プロバイダーを追加し、処理を完了します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-115">After the <xref:Microsoft.SqlServer.Dts.Runtime.DtsContainer.LoggingMode%2A> property is set to `Enabled`, a log provider is added to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection of the container to complete the process.</span></span> <span data-ttu-id="1db2e-116"><xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> オブジェクトでは <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> コレクションが使用可能で、これにはコンテナーで選択されたログ プロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="1db2e-116">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection is available on the <xref:Microsoft.SqlServer.Dts.Runtime.LoggingOptions> object, and contains the log providers selected for the container.</span></span> <span data-ttu-id="1db2e-117">プロバイダーを作成し、コレクションに追加するには、<xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-117">The <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders.Add%2A> method is called to create a provider and add it to the collection.</span></span> <span data-ttu-id="1db2e-118">このメソッドは、コレクションに追加されたログ プロバイダーを返します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-118">The method then returns the log provider that was added to the collection.</span></span> <span data-ttu-id="1db2e-119">それぞれのプロバイダーには、そのプロバイダーに特有の構成設定があります。これらのプロパティは、<xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> プロパティを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-119">Each provider has configuration settings that are unique to that provider, and these properties are set using the <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> property.</span></span>

 <span data-ttu-id="1db2e-120">次の表に、使用可能なログ プロバイダー、説明、および <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> 情報を示します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-120">The following table lists the available log providers, their description, and their <xref:Microsoft.SqlServer.Dts.Runtime.LogProvider.ConfigString%2A> information.</span></span>

|<span data-ttu-id="1db2e-121">プロバイダー</span><span class="sxs-lookup"><span data-stu-id="1db2e-121">Provider</span></span>|<span data-ttu-id="1db2e-122">説明</span><span class="sxs-lookup"><span data-stu-id="1db2e-122">Description</span></span>|<span data-ttu-id="1db2e-123">ConfigString プロパティ</span><span class="sxs-lookup"><span data-stu-id="1db2e-123">ConfigString property</span></span>|
|--------------|-----------------|---------------------------|
|<span data-ttu-id="1db2e-124">SQL Server プロファイラー</span><span class="sxs-lookup"><span data-stu-id="1db2e-124">SQL Server Profiler</span></span>|<span data-ttu-id="1db2e-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler でキャプチャおよび表示される SQL トレースを生成します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-125">Generates SQL traces that may be captured and viewed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Profiler.</span></span> <span data-ttu-id="1db2e-126">このプロバイダーで使用されるファイル名の既定の拡張子は、.trc です。</span><span class="sxs-lookup"><span data-stu-id="1db2e-126">The default file name extension for this provider is .trc.</span></span>|<span data-ttu-id="1db2e-127">構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1db2e-127">No configuration is required.</span></span>|
|<span data-ttu-id="1db2e-128">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1db2e-128">SQL Server</span></span>|<span data-ttu-id="1db2e-129">イベント ログ エントリを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースの **sysssislog** テーブルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-129">Writes event log entries to the **sysssislog** table in any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1db2e-130">プロバイダーの場合は、データベースへの接続と対象データベースの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1db2e-130">provider requires that the connection to the database be specified, and also the target database name.</span></span>|
|<span data-ttu-id="1db2e-131">テキスト ファイル</span><span class="sxs-lookup"><span data-stu-id="1db2e-131">Text File</span></span>|<span data-ttu-id="1db2e-132">イベント ログ エントリをコンマ区切り (CSV) 形式で ASCII テキスト ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-132">Writes event log entries to ASCII text files in a comma-separated value (CSV) format.</span></span> <span data-ttu-id="1db2e-133">このプロバイダーで使用されるファイル名の既定の拡張子は、.log です。</span><span class="sxs-lookup"><span data-stu-id="1db2e-133">The default file name extension for this provider is .log.</span></span>|<span data-ttu-id="1db2e-134">ファイル接続マネージャーの名前。</span><span class="sxs-lookup"><span data-stu-id="1db2e-134">The name of a file connection manager.</span></span>|
|<span data-ttu-id="1db2e-135">Windows イベント ログ</span><span class="sxs-lookup"><span data-stu-id="1db2e-135">Windows Event Log</span></span>|<span data-ttu-id="1db2e-136">ローカル コンピューター上のアプリケーション ログの標準 Windows イベント ログにログを記録します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-136">Logs to standard Windows Event Log on the local computer in the Application log.</span></span>|<span data-ttu-id="1db2e-137">構成は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="1db2e-137">No configuration is required.</span></span>|
|<span data-ttu-id="1db2e-138">XML ファイル</span><span class="sxs-lookup"><span data-stu-id="1db2e-138">XML File</span></span>|<span data-ttu-id="1db2e-139">イベント ログ エントリを XML 形式ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-139">Writes event log entries to XML formatted file.</span></span> <span data-ttu-id="1db2e-140">このプロバイダーの既定のファイル名拡張子は .xml です。</span><span class="sxs-lookup"><span data-stu-id="1db2e-140">The default file name extension for this provider is .xml</span></span>|<span data-ttu-id="1db2e-141">ファイル接続マネージャーの名前。</span><span class="sxs-lookup"><span data-stu-id="1db2e-141">The name of a file connection manager.</span></span>|

 <span data-ttu-id="1db2e-142">イベント ログにイベントを含めたり除外するには、コンテナーの `EventFilterKind` プロパティおよび `EventFilter` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-142">Events are included in or excluded from the event log by setting the `EventFilterKind` and the `EventFilter` properties of the container.</span></span> <span data-ttu-id="1db2e-143">`EventFilterKind` 構造には `ExclusionFilter` および `InclusionFilter` の 2 つの値があります。これはそれぞれ、`EventFilter` に追加されたイベントが、イベント ログに含まれるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-143">The `EventFilterKind` structure contains two values, `ExclusionFilter` and `InclusionFilter`, that indicate whether the events that are added to the `EventFilter` are included in the event log.</span></span> <span data-ttu-id="1db2e-144">次に、フィルター選択の対象となるイベントの名前を含む文字配列を `EventFilter` プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="1db2e-144">The `EventFilter` property is then assigned a string array that contains the names of the events that are the subject of the filtering.</span></span>

 <span data-ttu-id="1db2e-145">次のコードは、パッケージのログ記録を有効にし、<xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> コレクションにテキスト ファイルのログ プロバイダーを追加し、ログ出力に含めるイベントの一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-145">The following code enables logging on a package, adds the log provider for Text files to the <xref:Microsoft.SqlServer.Dts.Runtime.SelectedLogProviders> collection, and specifies a list of events to include in the logging output.</span></span>

## <a name="sample"></a><span data-ttu-id="1db2e-146">サンプル</span><span class="sxs-lookup"><span data-stu-id="1db2e-146">Sample</span></span>

```csharp
using System;
using Microsoft.SqlServer.Dts.Runtime;

namespace Microsoft.SqlServer.Dts.Samples
{
  class Program
  {
    static void Main(string[] args)
    {
      Package p = new Package();

      ConnectionManager loggingConnection = p.Connections.Add("FILE");
      loggingConnection.ConnectionString = @"C:\SSISPackageLog.txt";

      LogProvider provider = p.LogProviders.Add("DTS.LogProviderTextFile.2");
      provider.ConfigString = loggingConnection.Name;
      p.LoggingOptions.SelectedLogProviders.Add(provider);
      p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion;
      p.LoggingOptions.EventFilter = new String[] { "OnPreExecute", 
         "OnPostExecute", "OnError", "OnWarning", "OnInformation" };
      p.LoggingMode = DTSLoggingMode.Enabled;

      // Add tasks and other objects to the package.

    }
  }
}
```

```vb
Imports Microsoft.SqlServer.Dts.Runtime

Module Module1

  Sub Main()

    Dim p As Package = New Package()

    Dim loggingConnection As ConnectionManager = p.Connections.Add("FILE")
    loggingConnection.ConnectionString = "C:\SSISPackageLog.txt"

    Dim provider As LogProvider = p.LogProviders.Add("DTS.LogProviderTextFile.2")
    provider.ConfigString = loggingConnection.Name
    p.LoggingOptions.SelectedLogProviders.Add(provider)
    p.LoggingOptions.EventFilterKind = DTSEventFilterKind.Inclusion
    p.LoggingOptions.EventFilter = New String() {"OnPreExecute", _
       "OnPostExecute", "OnError", "OnWarning", "OnInformation"}
    p.LoggingMode = DTSLoggingMode.Enabled

    ' Add tasks and other objects to the package.

  End Sub

End Module
```

<span data-ttu-id="1db2e-147">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="1db2e-147">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="1db2e-148">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1db2e-148">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="1db2e-149">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="1db2e-149">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="1db2e-150">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="1db2e-150">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1db2e-151">参照</span><span class="sxs-lookup"><span data-stu-id="1db2e-151">See Also</span></span>
 [<span data-ttu-id="1db2e-152">Integration Services &#40;SSIS&#41; のログ記録</span><span class="sxs-lookup"><span data-stu-id="1db2e-152">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)


