---
title: パッケージ実行用のダンプ ファイルを生成する | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 61ef1731-cb3a-4afb-b4a4-059b04aeade0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 61e511aaff6c3c77338211537a685f8a1dc82981
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631141"
---
# <a name="generating-dump-files-for-package-execution"></a><span data-ttu-id="91960-102">パッケージ実行用のダンプ ファイルを生成する</span><span class="sxs-lookup"><span data-stu-id="91960-102">Generating Dump Files for Package Execution</span></span>
  <span data-ttu-id="91960-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]では、パッケージの実行に関する情報を提供するデバッグ ダンプ ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="91960-103">In [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you can create debug dump files that provide information about the execution of a package.</span></span> <span data-ttu-id="91960-104">このファイル内の情報は、パッケージの実行に関する問題のトラブルシューティングに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="91960-104">The information in these files can help you in troubleshooting package execution issues.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="91960-105">デバッグ ダンプ ファイルには機密情報が含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="91960-105">Debug dump files might contain sensitive information.</span></span> <span data-ttu-id="91960-106">機密情報を保護するには、アクセス制御リスト (ACL) を使用してこのファイルへのアクセスを制限するか、アクセスが制限されたフォルダーにファイルをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="91960-106">To help protect sensitive information, you can use an access control list (ACL) to restrict access to the files, or copy the files to a folder that has restricted access.</span></span> <span data-ttu-id="91960-107">たとえば、デバッグ ファイルを [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポート サービスに送信する前には、機密性の高い情報をすべて削除することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="91960-107">For example, before you send your debug files to [!INCLUDE[msCoName](../../includes/msconame-md.md)] support services, we recommend that you remove any sensitive or confidential information.</span></span>  
  
 <span data-ttu-id="91960-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーにプロジェクトを配置すると、そのプロジェクトに含まれているパッケージの実行に関する情報を提供するダンプ ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="91960-108">When you deploy a project to the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] server, you can create dump files that provide information about the execution of the packages contained in the project.</span></span> <span data-ttu-id="91960-109">ISServerExec.exe プロセスが終了すると、ダンプ ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="91960-109">When the ISServerExec.exe process ends, the dump files are created.</span></span> <span data-ttu-id="91960-110">**[パッケージの実行]** ダイアログ ボックスの **[エラー時にダンプする]** オプションを選択することにより、パッケージの実行中にエラーが発生したらダンプ ファイルが作成されるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="91960-110">You can specify that a dump file is created when errors occur during the package execution, by selecting the **Dump on errors** option in the **Execute Package** Dialog box.</span></span> <span data-ttu-id="91960-111">また、次のストアド プロシージャを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="91960-111">You can also use the following stored procedures:</span></span>  
  
-   [<span data-ttu-id="91960-112">catalog.set_execution_parameter_value &#40;SSISDB データベース&#41;</span><span class="sxs-lookup"><span data-stu-id="91960-112">catalog.set_execution_parameter_value &#40;SSISDB Database&#41;</span></span>](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
     <span data-ttu-id="91960-113">パッケージの実行中にエラーまたはイベントが発生したとき、および特定のイベントが発生したときにダンプ ファイルが作成されるように構成する場合に、このストアド プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="91960-113">Call this stored procedure to configure a dump file to be created when any error or event occurs, and when specific events occur, during a package execution.</span></span>  
  
-   [<span data-ttu-id="91960-114">catalog.create_execution_dump</span><span class="sxs-lookup"><span data-stu-id="91960-114">catalog.create_execution_dump</span></span>](/sql/integration-services/system-stored-procedures/catalog-create-execution-dump)  
  
     <span data-ttu-id="91960-115">実行中のパッケージを一時停止してダンプ ファイルを作成する場合に、このストアド プロシージャを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="91960-115">Call this stored procedure to cause a running package to pause and create a dump file.</span></span>  
  
 <span data-ttu-id="91960-116">パッケージ配置モデルを使用してパッケージを配置する場合は、**dtexec** ユーティリティまたは **dtutil** ユーティリティを使用して、コマンド ラインでデバッグ ダンプ オプションを指定することによって、デバッグ ダンプ ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="91960-116">If you are deploying packages using the package deployment model, you create the debug dump files by using either the **dtexec** utility or the **dtutil** utility to specify a debug dump option in the command line.</span></span> <span data-ttu-id="91960-117">詳細については、「 [dtexec ユーティリティ](../packages/dtexec-utility.md) 」と「 [dtutil ユーティリティ](../dtutil-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91960-117">For more information, see [dtexec Utility](../packages/dtexec-utility.md) and [dtutil Utility](../dtutil-utility.md).</span></span> <span data-ttu-id="91960-118">パッケージ配置モデルの詳細については、「[プロジェクトとパッケージの配置](../packages/deploy-integration-services-ssis-projects-and-packages.md)」および「 [SSIS&#41;&#40;パッケージ配置](../packages/legacy-package-deployment-ssis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="91960-118">For more information about the package deployment model, see [Deployment of Projects and Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md) and [Package Deployment &#40;SSIS&#41;](../packages/legacy-package-deployment-ssis.md).</span></span>  
  
## <a name="debug-dump-file-format"></a><span data-ttu-id="91960-119">デバッグ ダンプ ファイルの形式</span><span class="sxs-lookup"><span data-stu-id="91960-119">Debug Dump File Format</span></span>  
 <span data-ttu-id="91960-120">デバッグ ダンプ オプションを指定した場合、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって作成されるデバッグ ダンプ ファイルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="91960-120">When you specify a debug dump option, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates the following debug dump files:</span></span>  
  
-   <span data-ttu-id="91960-121">.mdmp デバッグ ダンプ ファイル。</span><span class="sxs-lookup"><span data-stu-id="91960-121">A .mdmp debug dump file.</span></span> <span data-ttu-id="91960-122">これはバイナリ ファイルです。</span><span class="sxs-lookup"><span data-stu-id="91960-122">This is a binary file.</span></span>  
  
-   <span data-ttu-id="91960-123">.tmp デバッグ ダンプ ファイル。</span><span class="sxs-lookup"><span data-stu-id="91960-123">The .tmp debug dump file.</span></span> <span data-ttu-id="91960-124">これはテキスト形式のファイルです。</span><span class="sxs-lookup"><span data-stu-id="91960-124">This is a text formatted file.</span></span>  
  
 <span data-ttu-id="91960-125">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の既定では、これらのファイルは *\<drive>:* \Program Files\Microsoft SQL Server\110\Shared\ErrorDumps フォルダーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="91960-125">By default, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stores these files in the folder, *\<drive>:* \Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.</span></span>  
  
 <span data-ttu-id="91960-126">次の表では、.tmp ファイル内の特定のセクションのみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="91960-126">The following table describes only certain sections in the .tmp file.</span></span> <span data-ttu-id="91960-127">.tmp ファイルには、次の表に記載されていないデータが他にも含まれています。</span><span class="sxs-lookup"><span data-stu-id="91960-127">The .tmp file includes additional data that is not listed in the table.</span></span>  
  
|<span data-ttu-id="91960-128">情報の種類</span><span class="sxs-lookup"><span data-stu-id="91960-128">Type of information</span></span>|<span data-ttu-id="91960-129">説明</span><span class="sxs-lookup"><span data-stu-id="91960-129">Description</span></span>|<span data-ttu-id="91960-130">例</span><span class="sxs-lookup"><span data-stu-id="91960-130">Example</span></span>|  
|-------------------------|-----------------|-------------|  
|<span data-ttu-id="91960-131">環境</span><span class="sxs-lookup"><span data-stu-id="91960-131">Environment</span></span>|<span data-ttu-id="91960-132">オペレーティング システムのバージョン、メモリの使用量のデータ、プロセス ID、およびプロセス イメージ名。</span><span class="sxs-lookup"><span data-stu-id="91960-132">Operating system version, memory usage data, process ID, and process image name.</span></span> <span data-ttu-id="91960-133">環境情報は .tmp ファイルの先頭にあります。</span><span class="sxs-lookup"><span data-stu-id="91960-133">The environment information is at the beginning of the .tmp file.</span></span>|<span data-ttu-id="91960-134"># SSIS Textual Dump taken at 9/13/2007 1:50:34 PM</span><span class="sxs-lookup"><span data-stu-id="91960-134"># SSIS Textual Dump taken at 9/13/2007 1:50:34 PM</span></span><br /><br /> <span data-ttu-id="91960-135">#PID 4120</span><span class="sxs-lookup"><span data-stu-id="91960-135">#PID 4120</span></span><br /><br /> <span data-ttu-id="91960-136">#Image Name [C:\Program Files\Microsoft SQL Server\110\DTS\Binn\DTExec.exe]</span><span class="sxs-lookup"><span data-stu-id="91960-136">#Image Name [C:\Program Files\Microsoft SQL Server\110\DTS\Binn\DTExec.exe]</span></span><br /><br /> <span data-ttu-id="91960-137"># OS major=6 minor=0 build=6000</span><span class="sxs-lookup"><span data-stu-id="91960-137"># OS major=6 minor=0 build=6000</span></span><br /><br /> <span data-ttu-id="91960-138"># Running on 2 amd64 processors under WOW64</span><span class="sxs-lookup"><span data-stu-id="91960-138"># Running on 2 amd64 processors under WOW64</span></span><br /><br /> <span data-ttu-id="91960-139"># Memory:58% in use.</span><span class="sxs-lookup"><span data-stu-id="91960-139"># Memory: 58% in use.</span></span> <span data-ttu-id="91960-140">Physical:845M/2044M  Paging:2404M/4095M (avail/total)</span><span class="sxs-lookup"><span data-stu-id="91960-140">Physical: 845M/2044M  Paging: 2404M/4095M (avail/total)</span></span>|  
|<span data-ttu-id="91960-141">ダイナミック リンク ライブラリ (DLL) のパスとバージョン</span><span class="sxs-lookup"><span data-stu-id="91960-141">Dynamic-link library (DLL) path and version</span></span>|<span data-ttu-id="91960-142">パッケージの処理中にシステムによって読み込まれる各 DLL のパスとバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="91960-142">Path and version number of each DLL that the system loads during the processing of a package.</span></span>|<span data-ttu-id="91960-143"># Loaded Module: c:\bb\Sql\DTS\src\bin\debug\i386\DTExec.exe (10.0.1069.5)</span><span class="sxs-lookup"><span data-stu-id="91960-143"># Loaded Module: c:\bb\Sql\DTS\src\bin\debug\i386\DTExec.exe (10.0.1069.5)</span></span><br /><br /> <span data-ttu-id="91960-144"># Loaded Module:C:\Windows\SysWOW64\ntdll.dll (6.0.6000.16386)</span><span class="sxs-lookup"><span data-stu-id="91960-144"># Loaded Module: C:\Windows\SysWOW64\ntdll.dll (6.0.6000.16386)</span></span><br /><br /> <span data-ttu-id="91960-145"># Loaded Module:C:\Windows\syswow64\kernel32.dll (6.0.6000.16386)</span><span class="sxs-lookup"><span data-stu-id="91960-145"># Loaded Module: C:\Windows\syswow64\kernel32.dll (6.0.6000.16386)</span></span>|  
|<span data-ttu-id="91960-146">最新のメッセージ</span><span class="sxs-lookup"><span data-stu-id="91960-146">Recent messages</span></span>|<span data-ttu-id="91960-147">システムで発行された最新のメッセージ。</span><span class="sxs-lookup"><span data-stu-id="91960-147">Recent messages issued by the system.</span></span> <span data-ttu-id="91960-148">各メッセージの時刻、種類、説明、およびスレッド ID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="91960-148">Includes the time, type, description, and thread ID of each message.</span></span>|<span data-ttu-id="91960-149">[M:1]   Ring buffer entry:              (\*pRecord)</span><span class="sxs-lookup"><span data-stu-id="91960-149">[M:1]   Ring buffer entry:              (\*pRecord)</span></span><br /><br /> <span data-ttu-id="91960-150">[D:2]      <<\<CRingBufferLogging::RingBufferLoggingRecord>>> ( \@ 0282F1A8 )</span><span class="sxs-lookup"><span data-stu-id="91960-150">[D:2]      <<\<CRingBufferLogging::RingBufferLoggingRecord>>> ( \@ 0282F1A8 )</span></span><br /><br /> <span data-ttu-id="91960-151">[E:3]         Time Stamp:2007-09-13 13:50:32.786      (szTimeStamp)</span><span class="sxs-lookup"><span data-stu-id="91960-151">[E:3]         Time Stamp: 2007-09-13 13:50:32.786      (szTimeStamp)</span></span><br /><br /> <span data-ttu-id="91960-152">[E:3]         Thread ID:2368           (ThreadID)</span><span class="sxs-lookup"><span data-stu-id="91960-152">[E:3]         Thread ID: 2368           (ThreadID)</span></span><br /><br /> <span data-ttu-id="91960-153">[E:3]         Event Name:OnError                        (EventName)</span><span class="sxs-lookup"><span data-stu-id="91960-153">[E:3]         Event Name: OnError                        (EventName)</span></span><br /><br /> <span data-ttu-id="91960-154">[E:3]         Source Name:              (SourceName)</span><span class="sxs-lookup"><span data-stu-id="91960-154">[E:3]         Source Name:                (SourceName)</span></span><br /><br /> <span data-ttu-id="91960-155">[E:3]         Source ID:                      (SourceID)</span><span class="sxs-lookup"><span data-stu-id="91960-155">[E:3]         Source ID:                        (SourceID)</span></span><br /><br /> <span data-ttu-id="91960-156">[E:3]         Execution ID:               (ExecutionGUID)</span><span class="sxs-lookup"><span data-stu-id="91960-156">[E:3]         Execution ID:                 (ExecutionGUID)</span></span><br /><br /> <span data-ttu-id="91960-157">[E:3]         Data Code: -1073446879              (DataCode)</span><span class="sxs-lookup"><span data-stu-id="91960-157">[E:3]         Data Code: -1073446879              (DataCode)</span></span><br /><br /> <span data-ttu-id="91960-158">[E:3]         Description:コンポーネントが見つからないか、登録されていないか、アップグレードできないか、コンポーネントに必要なインターフェイスが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="91960-158">[E:3]         Description: The component is missing, not registered, not upgradeable, or missing required interfaces.</span></span> <span data-ttu-id="91960-159">このコンポーネントの連絡先情報は "" です。</span><span class="sxs-lookup"><span data-stu-id="91960-159">The contact information for this component is "".</span></span>|  
  
## <a name="related-content"></a><span data-ttu-id="91960-160">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="91960-160">Related Content</span></span>  
 <span data-ttu-id="91960-161">[[パッケージの実行] ダイアログ ボックス](../execute-package-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="91960-161">[Execute Package Dialog Box](../execute-package-dialog-box.md)</span></span>  
  
  