---
title: ReportingServicesService 構成ファイル | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- traces [Reporting Services]
- Report Server Windows service, ReportingServicesService configuration file
- ReportingServicesService configuration file
ms.assetid: 40f4a401-cb61-4c42-b1ec-01acdacdacd1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5124631db9635211827dd3b1abbff7116101a61d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641450"
---
# <a name="reportingservicesservice-configuration-file"></a><span data-ttu-id="93f97-102">ReportingServicesService 構成ファイル</span><span class="sxs-lookup"><span data-stu-id="93f97-102">ReportingServicesService Configuration File</span></span>
  <span data-ttu-id="93f97-103">ReportingServicesService.exe.config ファイルには、トレースを構成する設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="93f97-103">The ReportingServicesService.exe.config file includes settings that configure tracing.</span></span>  
  
## <a name="file-location"></a><span data-ttu-id="93f97-104">ファイルの場所</span><span class="sxs-lookup"><span data-stu-id="93f97-104">File Location</span></span>  
 <span data-ttu-id="93f97-105">このファイルは、\Reporting Services\Report Server\Bin フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="93f97-105">This file is located in the \Reporting Services\Report Server\Bin folder.</span></span>  
  
## <a name="editing-guidelines"></a><span data-ttu-id="93f97-106">編集のガイドライン</span><span class="sxs-lookup"><span data-stu-id="93f97-106">Editing Guidelines</span></span>  
 <span data-ttu-id="93f97-107">このファイルを変更して、ログ ファイル名を変更したり、トレース レベルを増減させることができます。</span><span class="sxs-lookup"><span data-stu-id="93f97-107">You can modify this file to rename the log file or to increase or decrease trace levels.</span></span> <span data-ttu-id="93f97-108">その他の設定は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="93f97-108">Do not modify any of the other settings.</span></span> <span data-ttu-id="93f97-109">手順については、「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93f97-109">For instructions, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="93f97-110">トレース ログの詳細については、「 [レポート サーバー サービスのトレース ログ](report-server-service-trace-log.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93f97-110">For more information about trace logs, see [Report Server Service Trace Log](report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="93f97-111">構成の例</span><span class="sxs-lookup"><span data-stu-id="93f97-111">Example Configuration</span></span>  
 <span data-ttu-id="93f97-112">ReportingServicesService.exe.config ファイルにある設定および既定値の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="93f97-112">The following example shows the settings and default values found in the ReportingServicesService.exe.config file.</span></span>  
  
```  
<configSections>  
      <section name="RStrace" type="Microsoft.ReportingServices.Diagnostics.RSTraceSectionHandler,Microsoft.ReportingServices.Diagnostics" />  
</configSections>  
<system.diagnostics>  
      <switches>  
          <add name="DefaultTraceSwitch" value="3" />  
      </switches>  
</system.diagnostics>  
<RStrace>  
      <add name="FileName" value="ReportServerService_" />  
      <add name="FileSizeLimitMb" value="32" />  
      <add name="KeepFilesForDays" value="14" />  
      <add name="Prefix" value="tid, time" />  
      <add name="TraceListeners" value="debugwindow, file" />  
      <add name="TraceFileMode" value="unique" />  
      <add name="Components" value="all" />  
</RStrace>  
<runtime>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
             <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.ReportingServices.Interfaces"  
                        publicKeyToken="89845dcd8080cc91"  
                        culture="neutral" />  
                    <bindingRedirect oldVersion="8.0.242.0"  
                                     newVersion="10.0.0.0"/>  
                    <bindingRedirect oldVersion="9.0.242.0"  
                                     newVersion="10.0.0.0"/>  
             </dependentAssembly>  
      </assemblyBinding>  
      <gcServer enabled="true" />  
</runtime>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="93f97-113">構成設定</span><span class="sxs-lookup"><span data-stu-id="93f97-113">Configuration Settings</span></span>  
 <span data-ttu-id="93f97-114">次の表では、特定の設定に関する情報を示します。</span><span class="sxs-lookup"><span data-stu-id="93f97-114">The following table provides information about specific settings.</span></span> <span data-ttu-id="93f97-115">構成ファイルに出現する順に、設定を示します。</span><span class="sxs-lookup"><span data-stu-id="93f97-115">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="93f97-116">設定</span><span class="sxs-lookup"><span data-stu-id="93f97-116">Setting</span></span>|<span data-ttu-id="93f97-117">説明</span><span class="sxs-lookup"><span data-stu-id="93f97-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93f97-118">**RStrace**</span><span class="sxs-lookup"><span data-stu-id="93f97-118">**RStrace**</span></span>|<span data-ttu-id="93f97-119">エラーおよびトレースに使用される名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-119">Specifies namespaces used for errors and tracing.</span></span>|  
|<span data-ttu-id="93f97-120">**DefaultTraceSwitch**</span><span class="sxs-lookup"><span data-stu-id="93f97-120">**DefaultTraceSwitch**</span></span>|<span data-ttu-id="93f97-121">ReportServerService トレース ログにレポートされる情報のレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-121">Specifies the level of information that is reported to the ReportServerService trace log.</span></span> <span data-ttu-id="93f97-122">各レベルには、そのレベルより低いすべてのレベルでレポートされる情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="93f97-122">Each level includes the information reported by all lower-numbered levels.</span></span> <span data-ttu-id="93f97-123">トレースを無効にすることはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="93f97-123">Disabling tracing is not recommended.</span></span> <span data-ttu-id="93f97-124">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="93f97-124">Valid values include:</span></span><br /><br /> <span data-ttu-id="93f97-125">0= トレースの無効化</span><span class="sxs-lookup"><span data-stu-id="93f97-125">0= Disables tracing</span></span><br /><br /> <span data-ttu-id="93f97-126">1= 例外および再起動</span><span class="sxs-lookup"><span data-stu-id="93f97-126">1= Exceptions and restarts</span></span><br /><br /> <span data-ttu-id="93f97-127">2= 例外、再起動、警告</span><span class="sxs-lookup"><span data-stu-id="93f97-127">2= Exceptions, restarts, warnings</span></span><br /><br /> <span data-ttu-id="93f97-128">3= 例外、再起動、警告、状態メッセージ (既定)</span><span class="sxs-lookup"><span data-stu-id="93f97-128">3= Exceptions, restarts, warnings, status messages (default)</span></span><br /><br /> <span data-ttu-id="93f97-129">4= 詳細モード</span><span class="sxs-lookup"><span data-stu-id="93f97-129">4= Verbose mode</span></span>|  
|<span data-ttu-id="93f97-130">**FileName**</span><span class="sxs-lookup"><span data-stu-id="93f97-130">**FileName**</span></span>|<span data-ttu-id="93f97-131">ログ ファイル名の最初の部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-131">Specifies the first portion of the log file name.</span></span> <span data-ttu-id="93f97-132">`Prefix` で指定した値が付加されて、完全な名前になります。</span><span class="sxs-lookup"><span data-stu-id="93f97-132">The value specified by `Prefix` completes the rest of the name.</span></span> <span data-ttu-id="93f97-133">既定では、この名前は ReportServerService_ です。</span><span class="sxs-lookup"><span data-stu-id="93f97-133">By default, the name is ReportServerService_.</span></span>|  
|<span data-ttu-id="93f97-134">**FileSizeLimitMb**</span><span class="sxs-lookup"><span data-stu-id="93f97-134">**FileSizeLimitMb**</span></span>|<span data-ttu-id="93f97-135">トレース ログのサイズの上限を指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-135">Specifies an upper limit on trace log size.</span></span> <span data-ttu-id="93f97-136">ファイルは MB 単位で測定されます。</span><span class="sxs-lookup"><span data-stu-id="93f97-136">The file is measured in megabytes.</span></span> <span data-ttu-id="93f97-137">正しい値は、0 から整数型の最大値までです。</span><span class="sxs-lookup"><span data-stu-id="93f97-137">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="93f97-138">既定値は 32 です。</span><span class="sxs-lookup"><span data-stu-id="93f97-138">The default value is 32.</span></span>|  
|<span data-ttu-id="93f97-139">**KeepFilesForDays**</span><span class="sxs-lookup"><span data-stu-id="93f97-139">**KeepFilesForDays**</span></span>|<span data-ttu-id="93f97-140">トレース ログ ファイルを削除するまでの保持期間を日数で指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-140">Specifies the number of days after which a trace log file will be deleted.</span></span> <span data-ttu-id="93f97-141">正しい値は、0 から整数型の最大値までです。</span><span class="sxs-lookup"><span data-stu-id="93f97-141">Valid values are 0 to a maximum integer.</span></span> <span data-ttu-id="93f97-142">既定値は 14 です。</span><span class="sxs-lookup"><span data-stu-id="93f97-142">The default value is 14.</span></span>|  
|`Prefix`|<span data-ttu-id="93f97-143">あるログのインスタンスを別のログのインスタンスと区別するために生成する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-143">Specifies a generated value that distinguishes one log instance from another.</span></span> <span data-ttu-id="93f97-144">既定では、トレース ログ ファイル名にタイムスタンプの値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="93f97-144">By default, timestamp values are appended to trace log file names.</span></span> <span data-ttu-id="93f97-145">この値は、" tid, time " に設定されます。</span><span class="sxs-lookup"><span data-stu-id="93f97-145">This value is set to " tid, time ".</span></span> <span data-ttu-id="93f97-146">この設定は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="93f97-146">Do not modify this setting.</span></span>|  
|<span data-ttu-id="93f97-147">**TraceListeners**</span><span class="sxs-lookup"><span data-stu-id="93f97-147">**TraceListeners**</span></span>|<span data-ttu-id="93f97-148">トレース ログ コンテンツの出力先を指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-148">Specifies a target for outputting trace log content.</span></span> <span data-ttu-id="93f97-149">複数の出力先を指定する場合、各出力先をコンマで区切ってください。</span><span class="sxs-lookup"><span data-stu-id="93f97-149">You can specify multiple targets using a comma to separate each one.</span></span> <span data-ttu-id="93f97-150">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="93f97-150">Valid values include:</span></span><br /><br /> <span data-ttu-id="93f97-151">DebugWindow (既定値)</span><span class="sxs-lookup"><span data-stu-id="93f97-151">DebugWindow (default)</span></span><br /><br /> <span data-ttu-id="93f97-152">File (既定値)</span><span class="sxs-lookup"><span data-stu-id="93f97-152">File (default)</span></span><br /><br /> <span data-ttu-id="93f97-153">StdOut</span><span class="sxs-lookup"><span data-stu-id="93f97-153">StdOut</span></span>|  
|<span data-ttu-id="93f97-154">**TraceFileMode**</span><span class="sxs-lookup"><span data-stu-id="93f97-154">**TraceFileMode**</span></span>|<span data-ttu-id="93f97-155">トレース ログに 24 時間データを含めるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-155">Specifies whether trace logs contain data for a 24-hour period.</span></span> <span data-ttu-id="93f97-156">コンポーネントごとに、毎日 1 つ、一意のトレース ログが必要です。</span><span class="sxs-lookup"><span data-stu-id="93f97-156">You should have one unique trace log for each component on each day.</span></span> <span data-ttu-id="93f97-157">この値は、"Unique (既定値)" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="93f97-157">This value is set to "Unique (default)".</span></span> <span data-ttu-id="93f97-158">この値は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="93f97-158">Do not modify this value.</span></span>|  
|<span data-ttu-id="93f97-159">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="93f97-159">**Components**</span></span>|<span data-ttu-id="93f97-160">トレース ログを作成するコンポーネントを指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-160">Specifies the components for which trace logs are created.</span></span> <span data-ttu-id="93f97-161">既定値は `all` です。</span><span class="sxs-lookup"><span data-stu-id="93f97-161">The default value is `all`.</span></span> <span data-ttu-id="93f97-162">この設定に対する他の有効な値には、内部コンポーネントの名前があります。</span><span class="sxs-lookup"><span data-stu-id="93f97-162">Other valid values for this setting include the names of internal components.</span></span> <span data-ttu-id="93f97-163">この値は変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="93f97-163">Do not modify this value.</span></span>|  
|<span data-ttu-id="93f97-164">**ランタイム**</span><span class="sxs-lookup"><span data-stu-id="93f97-164">**Runtime**</span></span>|<span data-ttu-id="93f97-165">以前のバージョンとの下位互換性をサポートする構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="93f97-165">Specifies configuration settings that support backward compatibility with the previous version.</span></span> <span data-ttu-id="93f97-166">Microsoft.ReportingServices.Interfaces の以前のバージョンを対象とする要求を新しいバージョンにリダイレクトするには、Runtime 設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="93f97-166">Runtime settings are used to redirect requests that target the previous version of Microsoft.ReportingServices.Interfaces to the new version.</span></span><br /><br /> <span data-ttu-id="93f97-167">このセクションの構成設定は、すべて [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] の製品ドキュメントで説明されています。</span><span class="sxs-lookup"><span data-stu-id="93f97-167">All of the configuration settings in this section are described in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] product documentation.</span></span> <span data-ttu-id="93f97-168">詳細については、MSDN Web サイトまたは [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] ドキュメントの「ランタイム設定スキーマ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93f97-168">For more information, search for "Runtime Schema Settings" on the MSDN Web site or in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] documentation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93f97-169">参照</span><span class="sxs-lookup"><span data-stu-id="93f97-169">See Also</span></span>  
 <span data-ttu-id="93f97-170">[Reporting Services 構成ファイル](reporting-services-configuration-files.md) </span><span class="sxs-lookup"><span data-stu-id="93f97-170">[Reporting Services Configuration Files](reporting-services-configuration-files.md) </span></span>  
 [<span data-ttu-id="93f97-171">Report Server Service Trace Log</span><span class="sxs-lookup"><span data-stu-id="93f97-171">Report Server Service Trace Log</span></span>](report-server-service-trace-log.md)  
  
  
