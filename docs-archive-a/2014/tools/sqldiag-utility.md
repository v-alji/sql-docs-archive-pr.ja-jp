---
title: SQLdiag ユーティリティ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server], SQLdiag
- stopping diagnostic collection
- storing diagnostic information
- performance [SQL Server], diagnostic collection
- diagnostic records [SQL Server]
- scripts [SQL Server], diagnostic collection
- logs [SQL Server], diagnostic collection
- starting diagnostic collection
- clustered instance of SQL Server
- monitoring performance [SQL Server], diagnostic collection
- security [SQL Server], diagnostic collection
- SQLDIAG service
- space [SQL Server], diagnostic collection
- SQLdiag utility
- disk space [SQL Server], diagnostic collection
- configuration files [SQL Server]
- automatic diagnostic collection
- clusters [SQL Server], diagnostic collection
ms.assetid: 45ba1307-33d1-431e-872c-a6e4556f5ff2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0559e0b2261ed5ba1c9c384608d04194d685f695
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711241"
---
# <a name="sqldiag-utility"></a><span data-ttu-id="55a51-102">SQLdiag ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="55a51-102">SQLdiag Utility</span></span>
  <span data-ttu-id="55a51-103">**SQLdiag** ユーティリティは、コンソール アプリケーションまたはサービスとして実行できる汎用的な診断収集ユーティリティです。</span><span class="sxs-lookup"><span data-stu-id="55a51-103">The **SQLdiag** utility is a general purpose diagnostics collection utility that can be run as a console application or as a service.</span></span> <span data-ttu-id="55a51-104">**SQLdiag** を使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] やその他の種類のサーバーからログ ファイルやデータ ファイルを収集したり、サーバーを一定期間にわたって監視したり、サーバーに関する特定の問題をトラブルシューティングしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="55a51-104">You can use **SQLdiag** to collect logs and data files from [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and other types of servers, and use it to monitor your servers over time or troubleshoot specific problems with your servers.</span></span> <span data-ttu-id="55a51-105">**SQLdiag** は、 [!INCLUDE[msCoName](../includes/msconame-md.md)] カスタマー サポート サービスによる診断情報収集の高速化と簡素化も目的としています。</span><span class="sxs-lookup"><span data-stu-id="55a51-105">**SQLdiag** is intended to expedite and simplify diagnostic information gathering for [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-106">ユーティリティは変更できますが、そのコマンド ライン引数や動作に依存するアプリケーションやスクリプトは今後のリリースで正常に機能しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-106">This utility may be changed, and applications or scripts that rely on its command line arguments or behavior may not work correctly in future releases.</span></span>  
  
 <span data-ttu-id="55a51-107">**SQLdiag** が収集できる診断情報の種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="55a51-107">**SQLdiag** can collect the following types of diagnostic information:</span></span>  
  
-   <span data-ttu-id="55a51-108">Windows パフォーマンス ログ</span><span class="sxs-lookup"><span data-stu-id="55a51-108">Windows performance logs</span></span>  
  
-   <span data-ttu-id="55a51-109">Windows イベント ログ</span><span class="sxs-lookup"><span data-stu-id="55a51-109">Windows event logs</span></span>  
  
-   [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] <span data-ttu-id="55a51-110">トレース</span><span class="sxs-lookup"><span data-stu-id="55a51-110">traces</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="55a51-111">のブロッキング情報</span><span class="sxs-lookup"><span data-stu-id="55a51-111">blocking information</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="55a51-112">の構成情報</span><span class="sxs-lookup"><span data-stu-id="55a51-112">configuration information</span></span>  
  
 <span data-ttu-id="55a51-113">構成ファイル SQLDiag.xml を編集することで、 **SQLdiag** が収集する情報の種類を指定することができます。これについては、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="55a51-113">You can specify what types of information you want **SQLdiag** to collect by editing the configuration file SQLDiag.xml, which is described in a following section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a51-114">構文</span><span class="sxs-lookup"><span data-stu-id="55a51-114">Syntax</span></span>  
  
```  
  
      sqldiag   
     { [/?] }  
     |  
     { [/I configuration_file]  
       [/O output_folder_path]  
       [/Psupport_folder_path]  
       [/Noutput_folder_management_option]  
       [/Mmachine1 [ machine2machineN]| @machinelistfile]  
       [/Cfile_compression_type]  
       [/B [+]start_time]  
       [/E [+]stop_time]  
       [/ASQLdiag_application_name]  
       [/T { tcp [ ,port ] | np | lpc } ]  
       [/Q] [/G] [/R] [/U] [/L] [/X] }  
     |  
     { [START | STOP | STOP_ABORT] }  
     |  
     { [START | STOP | STOP_ABORT] /ASQLdiag_application_name }  
```  
  
## <a name="arguments"></a><span data-ttu-id="55a51-115">引数</span><span class="sxs-lookup"><span data-stu-id="55a51-115">Arguments</span></span>  
 <span data-ttu-id="55a51-116">**/?**</span><span class="sxs-lookup"><span data-stu-id="55a51-116">**/?**</span></span>  
 <span data-ttu-id="55a51-117">使用方法に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="55a51-117">Displays usage information.</span></span>  
  
 <span data-ttu-id="55a51-118">**/I** _configuration_file_</span><span class="sxs-lookup"><span data-stu-id="55a51-118">**/I** _configuration_file_</span></span>  
 <span data-ttu-id="55a51-119">**SQLdiag** が使用する構成ファイルを設定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-119">Sets the configuration file for **SQLdiag** to use.</span></span> <span data-ttu-id="55a51-120">既定では、 **/I** は SQLDiag.Xml に設定されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-120">By default, **/I** is set to SQLDiag.Xml.</span></span>  
  
 <span data-ttu-id="55a51-121">**/O** _output_folder_path_</span><span class="sxs-lookup"><span data-stu-id="55a51-121">**/O** _output_folder_path_</span></span>  
 <span data-ttu-id="55a51-122">**SQLdiag** 出力を、指定されたフォルダーにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="55a51-122">Redirects **SQLdiag** output to the specified folder.</span></span> <span data-ttu-id="55a51-123">**/O** オプションが指定されない場合、 **SQLdiag** 出力は、 **SQLdiag** スタートアップ フォルダーの下にある SQLDIAG という名前のサブフォルダーに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="55a51-123">If the **/O** option is not specified, **SQLdiag** output is written to a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="55a51-124">SQLDIAG フォルダーが存在しない場合、 **SQLdiag** によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-124">If the SQLDIAG folder does not exist, **SQLdiag** attempts to create it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-125">出力フォルダーの場所は、 **/P**で指定できるサポート フォルダーの場所に応じて決まります。</span><span class="sxs-lookup"><span data-stu-id="55a51-125">The output folder location is relative to the support folder location that can be specified with **/P**.</span></span> <span data-ttu-id="55a51-126">まったく別の場所に出力フォルダーを設定するには、 **/O**に完全なディレクトリ パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-126">To set an entirely different location for the output folder, specify the full directory path for **/O**.</span></span>  
  
 <span data-ttu-id="55a51-127">**/P** _support_folder_path_</span><span class="sxs-lookup"><span data-stu-id="55a51-127">**/P** _support_folder_path_</span></span>  
 <span data-ttu-id="55a51-128">サポート フォルダーのパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-128">Sets the support folder path.</span></span> <span data-ttu-id="55a51-129">既定では、 **/P** は **SQLdiag** 実行可能ファイルが存在するフォルダーに設定されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-129">By default, **/P** is set to the folder where the **SQLdiag** executable resides.</span></span> <span data-ttu-id="55a51-130">サポート フォルダーには、XML 構成ファイル、Transact-SQL スクリプト、診断情報の収集中にユーティリティが使用するその他のファイルなどの **SQLdiag** サポート ファイルが格納されています。</span><span class="sxs-lookup"><span data-stu-id="55a51-130">The support folder contains **SQLdiag** support files, such as the XML configuration file, Transact-SQL scripts, and other files that the utility uses during diagnostics collection.</span></span> <span data-ttu-id="55a51-131">このオプションを使用して、別のサポート ファイルのパスを指定すると、 **SQLdiag** は指定されたフォルダーに必要なサポート ファイルが存在しない場合、それらのファイルを指定されたフォルダーへ自動的にコピーします。</span><span class="sxs-lookup"><span data-stu-id="55a51-131">If you use this option to specify an alternate support files path, **SQLdiag** will automatically copy the support files it requires to the specified folder if they do not already exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-132">現在のフォルダーをサポート ファイルのパスとして設定するには、コマンド ラインの **%cd%** を次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-132">To set your current folder as the support path, specify **%cd%** on the command line as follows:</span></span>  
>   
>  <span data-ttu-id="55a51-133">**SQLDIAG /P %cd%**</span><span class="sxs-lookup"><span data-stu-id="55a51-133">**SQLDIAG /P %cd%**</span></span>  
  
 <span data-ttu-id="55a51-134">**/N** _output_folder_management_option_</span><span class="sxs-lookup"><span data-stu-id="55a51-134">**/N** _output_folder_management_option_</span></span>  
 <span data-ttu-id="55a51-135">起動時に **SQLdiag** が出力フォルダーを上書きまたは名前を変更するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-135">Sets whether **SQLdiag** overwrites or renames the output folder when it starts up.</span></span> <span data-ttu-id="55a51-136">使用できるオプションは</span><span class="sxs-lookup"><span data-stu-id="55a51-136">Available options:</span></span>  
  
 <span data-ttu-id="55a51-137">1 = 出力フォルダーを上書きします (既定)。</span><span class="sxs-lookup"><span data-stu-id="55a51-137">1 = Overwrites the output folder (default)</span></span>  
  
 <span data-ttu-id="55a51-138">2 = **SQLdiag** が起動したときに、SQLDIAG_00001、SQLDIAG_00002 のように、出力フォルダー名を変更します。</span><span class="sxs-lookup"><span data-stu-id="55a51-138">2 = When **SQLdiag** starts up, it renames the output folder to SQLDIAG_00001, SQLDIAG_00002, and so on.</span></span> <span data-ttu-id="55a51-139">現在の出力フォルダーの名前が変更された後に、 **SQLdiag** によって、既定の出力フォルダー SQLDIAG に出力が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="55a51-139">After renaming the current output folder, **SQLdiag** writes output to the default output folder SQLDIAG.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-140">**SQLdiag** は起動時に、現在の出力フォルダーに出力を追加しません。</span><span class="sxs-lookup"><span data-stu-id="55a51-140">**SQLdiag** does not append output to the current output folder when it starts up.</span></span> <span data-ttu-id="55a51-141">既定の出力フォルダーを上書きするか (オプション 1)、または既定のフォルダー名を変更して (オプション 2)、SQLDIAG という名前の新しい既定の出力フォルダーに出力を書き込むかのどちらかです。</span><span class="sxs-lookup"><span data-stu-id="55a51-141">It can only overwrite the default output folder (option 1) or rename the folder (option 2), and then it writes output to the new default output folder named SQLDIAG.</span></span>  
  
 <span data-ttu-id="55a51-142">**/M** _machine1_ [ *machine2 \* \*\* の場合] |*@machinelistfile\*</span><span class="sxs-lookup"><span data-stu-id="55a51-142">**/M** _machine1_ [ *machine2\*\*machineN*] | *@machinelistfile*</span></span>  
 <span data-ttu-id="55a51-143">構成ファイルで指定されたコンピューターをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="55a51-143">Overrides the machines specified in the configuration file.</span></span> <span data-ttu-id="55a51-144">既定では、構成ファイルは SQLDiag.Xml です。または **/I** パラメーターで設定されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-144">By default the configuration file is SQLDiag.Xml, or is set with the **/I** parameter.</span></span> <span data-ttu-id="55a51-145">複数のコンピューターを指定する場合、それぞれのコンピューター名をスペースで区切ります。</span><span class="sxs-lookup"><span data-stu-id="55a51-145">When specifying more than one machine, separate each machine name with a space.</span></span>  
  
 <span data-ttu-id="55a51-146">を使用 *@machinelistfile* すると、構成ファイルに格納されるコンピューターリストファイル名が指定されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-146">Using *@machinelistfile* specifies a machine list filename to be stored in the configuration file.</span></span>  
  
 <span data-ttu-id="55a51-147">**/C** _file_compression_type_</span><span class="sxs-lookup"><span data-stu-id="55a51-147">**/C** _file_compression_type_</span></span>  
 <span data-ttu-id="55a51-148">**SQLdiag** 出力フォルダー ファイルで使用されるファイル圧縮の種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-148">Sets the type of file compression used on the **SQLdiag** output folder files.</span></span> <span data-ttu-id="55a51-149">使用できるオプションは</span><span class="sxs-lookup"><span data-stu-id="55a51-149">Available options:</span></span>  
  
 <span data-ttu-id="55a51-150">0 = なし (既定)。</span><span class="sxs-lookup"><span data-stu-id="55a51-150">0 = none (default)</span></span>  
  
 <span data-ttu-id="55a51-151">1 = NTFS 圧縮を使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-151">1 = uses NTFS compression</span></span>  
  
 <span data-ttu-id="55a51-152">**/B** [ **+** ]*start_time*</span><span class="sxs-lookup"><span data-stu-id="55a51-152">**/B** [**+**]*start_time*</span></span>  
 <span data-ttu-id="55a51-153">診断データの収集を開始する日時は、</span><span class="sxs-lookup"><span data-stu-id="55a51-153">Specifies the date and time to start collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="55a51-154">YYYYMMDD_HH:MM:SS の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-154">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="55a51-155">時間は 24 時間形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-155">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="55a51-156">たとえば、午後 2:00 は</span><span class="sxs-lookup"><span data-stu-id="55a51-156">For example, 2:00 P.M.</span></span> <span data-ttu-id="55a51-157">は、 **14:00:00**と指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-157">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="55a51-158">現在の日時に対する相対時間を指定するには、日付を使用せず、HH:MM:SS の形式を使用して時間数を示し、 **+** を先頭に付加します。</span><span class="sxs-lookup"><span data-stu-id="55a51-158">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="55a51-159">たとえば、 **/B +02:00:00**と指定すると、 **SQLdiag** は情報収集を開始するまで 2 時間待機します。</span><span class="sxs-lookup"><span data-stu-id="55a51-159">For example, if you specify **/B +02:00:00**, **SQLdiag** will wait 2 hours before it starts collecting information.</span></span>  
  
 <span data-ttu-id="55a51-160">**+** と指定した *start_time*との間には空白を挿入しないでください。</span><span class="sxs-lookup"><span data-stu-id="55a51-160">Do not insert a space between **+** and the specified *start_time*.</span></span>  
  
 <span data-ttu-id="55a51-161">過去の時間を開始時間に指定すると、 **SQLdiag** は開始日を未来の開始日時に強制的に変更します。</span><span class="sxs-lookup"><span data-stu-id="55a51-161">If you specify a start time that is in the past, **SQLdiag** forcibly changes the start date so the start date and time are in the future.</span></span> <span data-ttu-id="55a51-162">たとえば、 **/B 01:00:00** を指定していて、現在の時間が 08:00:00 の場合、 **SQLdiag** はこの開始日を翌日の開始日に強制的に変更します。</span><span class="sxs-lookup"><span data-stu-id="55a51-162">For example, if you specify **/B 01:00:00** and the current time is 08:00:00, **SQLdiag** forcibly changes the start date so that the start date is the next day.</span></span>  
  
 <span data-ttu-id="55a51-163">**SQLdiag** は、ユーティリティが実行されているコンピューター上のローカル時間を使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="55a51-163">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="55a51-164">**/E** [ **+** ]*stop_time*</span><span class="sxs-lookup"><span data-stu-id="55a51-164">**/E** [**+**]*stop_time*</span></span>  
 <span data-ttu-id="55a51-165">診断データの収集を停止する日時は、</span><span class="sxs-lookup"><span data-stu-id="55a51-165">Specifies the date and time to stop collecting diagnostic data in the following format:</span></span>  
  
 <span data-ttu-id="55a51-166">YYYYMMDD_HH:MM:SS の形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-166">YYYYMMDD_HH:MM:SS</span></span>  
  
 <span data-ttu-id="55a51-167">時間は 24 時間形式で指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-167">The time is specified using 24-hour notation.</span></span> <span data-ttu-id="55a51-168">たとえば、午後 2:00 は</span><span class="sxs-lookup"><span data-stu-id="55a51-168">For example, 2:00 P.M.</span></span> <span data-ttu-id="55a51-169">は、 **14:00:00**と指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-169">should be specified as **14:00:00**.</span></span>  
  
 <span data-ttu-id="55a51-170">現在の日時に対する相対時間を指定するには、日付を使用せず、HH:MM:SS の形式を使用して時間数を示し、 **+** を先頭に付加します。</span><span class="sxs-lookup"><span data-stu-id="55a51-170">Use **+** without the date (HH:MM:SS only) to specify a time that is relative to the current date and time.</span></span> <span data-ttu-id="55a51-171">たとえば、 **/B +02:00:00 /E +03:00:00**を使用して開始時間と終了時間を指定すると、情報の収集を開始する前に **SQLdiag** は 2 時間待機し、それから情報の収集を 3 時間行い、停止して終了します。</span><span class="sxs-lookup"><span data-stu-id="55a51-171">For example, if you specify a start time and end time by using **/B +02:00:00 /E +03:00:00**, **SQLdiag** waits 2 hours before it starts collecting information, then collects information for 3 hours before it stops and exits.</span></span> <span data-ttu-id="55a51-172">**/B** が指定されない場合、 **SQLdiag** はすぐに診断情報の収集を開始し、 **/E**で指定された日時に終了します。</span><span class="sxs-lookup"><span data-stu-id="55a51-172">If **/B** is not specified, **SQLdiag** starts collecting diagnostics immediately and ends at the date and time specified by **/E**.</span></span>  
  
 <span data-ttu-id="55a51-173">**+** と指定した *start_time* または *end_time*との間には空白を挿入しないでください。</span><span class="sxs-lookup"><span data-stu-id="55a51-173">Do not insert a space between **+** and the specified *start_time* or *end_time*.</span></span>  
  
 <span data-ttu-id="55a51-174">**SQLdiag** は、ユーティリティが実行されているコンピューター上のローカル時間を使用することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="55a51-174">Note that **SQLdiag** uses the local time on the computer where the utility is running.</span></span>  
  
 <span data-ttu-id="55a51-175">**/A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="55a51-175">**/A** _SQLdiag_application_name_</span></span>  
 <span data-ttu-id="55a51-176">**SQLdiag** ユーティリティの複数のインスタンスの実行を、同一の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスに対して有効にします。</span><span class="sxs-lookup"><span data-stu-id="55a51-176">Enables running multiple instances of the **SQLdiag** utility against the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="55a51-177">各 *SQLdiag_application_name* は、異なるインスタンスの **SQLdiag**を特定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-177">Each *SQLdiag_application_name* identifies a different instance of **SQLdiag**.</span></span> <span data-ttu-id="55a51-178">*SQLdiag_application_name* インスタンスの名前と [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前には関連性はありません。</span><span class="sxs-lookup"><span data-stu-id="55a51-178">No relationship exists between a *SQLdiag_application_name* instance and a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance name.</span></span>  
  
 <span data-ttu-id="55a51-179">*SQLdiag_application_name* を使用すると、 **SQLdiag** サービスの特定のインスタンスを開始または停止できます。</span><span class="sxs-lookup"><span data-stu-id="55a51-179">*SQLdiag_application_name* can be used to start or stop a specific instance of the **SQLdiag** service.</span></span>  
  
 <span data-ttu-id="55a51-180">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="55a51-180">For example:</span></span>  
  
 <span data-ttu-id="55a51-181">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="55a51-181">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
 <span data-ttu-id="55a51-182">**/R** オプションと共に使用し、 **SQLdiag** の特定のインスタンスをサービスとして登録することもできます。</span><span class="sxs-lookup"><span data-stu-id="55a51-182">It can also be used with the **/R** option to register a specific instance of **SQLdiag** as a service.</span></span> <span data-ttu-id="55a51-183">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="55a51-183">For example:</span></span>  
  
 <span data-ttu-id="55a51-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="55a51-184">**SQLDIAG /R /A** _SQLdiag_application_name_</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-185">**SQLdiag** は *SQLdiag_application_name*に指定されたインスタンス名に、自動的にプレフィックスの DIAG$ を付けます。</span><span class="sxs-lookup"><span data-stu-id="55a51-185">**SQLdiag** automatically prefixes DIAG$ to the instance name specified for *SQLdiag_application_name*.</span></span> <span data-ttu-id="55a51-186">これにより、 **SQLdiag** をサービスとして登録する場合に、わかりやすいサービス名になります。</span><span class="sxs-lookup"><span data-stu-id="55a51-186">This provides a sensible service name if you register **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="55a51-187">/T { tcp [ ,*port* ] | np | lpc }</span><span class="sxs-lookup"><span data-stu-id="55a51-187">/T { tcp [ ,*port* ] | np | lpc }</span></span>  
 <span data-ttu-id="55a51-188">指定されたプロトコルを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="55a51-188">Connects to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] using the specified protocol.</span></span>  
  
 <span data-ttu-id="55a51-189">tcp [,*port*]</span><span class="sxs-lookup"><span data-stu-id="55a51-189">tcp [,*port*]</span></span>  
 <span data-ttu-id="55a51-190">伝送制御プロトコル/インターネット プロトコル (TCP/IP)。</span><span class="sxs-lookup"><span data-stu-id="55a51-190">Transmission Control Protocol/Internet Protocol (TCP/IP).</span></span> <span data-ttu-id="55a51-191">必要に応じて接続のポート番号を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="55a51-191">You can optionally specify a port number for the connection.</span></span>  
  
 <span data-ttu-id="55a51-192">np</span><span class="sxs-lookup"><span data-stu-id="55a51-192">np</span></span>  
 <span data-ttu-id="55a51-193">名前付きパイプ。</span><span class="sxs-lookup"><span data-stu-id="55a51-193">Named pipes.</span></span> <span data-ttu-id="55a51-194">既定で、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスは、名前付きインスタンスの名前付きパイプ `\\.\pipe\sql\query` および `\\.\pipe\MSSQL$<instancename>\sql\query` でリッスンします。</span><span class="sxs-lookup"><span data-stu-id="55a51-194">By default, the default instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] listens on named pipe `\\.\pipe\sql\query` and `\\.\pipe\MSSQL$<instancename>\sql\query` for a named instance.</span></span> <span data-ttu-id="55a51-195">代替パイプの名前を使用して、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続することはできません。</span><span class="sxs-lookup"><span data-stu-id="55a51-195">You cannot connect to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using an alternate pipe name.</span></span>  
  
 <span data-ttu-id="55a51-196">lpc</span><span class="sxs-lookup"><span data-stu-id="55a51-196">lpc</span></span>  
 <span data-ttu-id="55a51-197">ローカル プロシージャ コールです。</span><span class="sxs-lookup"><span data-stu-id="55a51-197">Local procedure call.</span></span> <span data-ttu-id="55a51-198">クライアントが、同じコンピューター上で [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスに接続している場合は、この共有メモリ プロトコルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="55a51-198">This shared memory protocol is available if the client is connecting to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the same computer.</span></span>  
  
 <span data-ttu-id="55a51-199">**/Q**</span><span class="sxs-lookup"><span data-stu-id="55a51-199">**/Q**</span></span>  
 <span data-ttu-id="55a51-200">**SQLdiag** を非表示モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="55a51-200">Runs **SQLdiag** in quiet mode.</span></span> <span data-ttu-id="55a51-201">**/Q** を使用すると、パスワード プロンプトなど、すべてのプロンプトが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="55a51-201">**/Q** suppresses all prompts, such as password prompts.</span></span>  
  
 <span data-ttu-id="55a51-202">**/G**</span><span class="sxs-lookup"><span data-stu-id="55a51-202">**/G**</span></span>  
 <span data-ttu-id="55a51-203">**SQLdiag** を汎用モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="55a51-203">Runs **SQLdiag** in generic mode.</span></span> <span data-ttu-id="55a51-204">**/G** が指定されていると、 **SQLdiag** はスタートアップ時に、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の接続チェックやユーザーが **sysadmin** 固定サーバー ロールのメンバーであることの確認を行いません。</span><span class="sxs-lookup"><span data-stu-id="55a51-204">When **/G** is specified, on startup **SQLdiag** does not enforce [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] connectivity checks or verify that the user is a member of the **sysadmin** fixed server role.</span></span> <span data-ttu-id="55a51-205">その代わり、 **SQLdiag** は、要求された各診断情報を収集するための適切な権限をユーザーが持っているかどうかの判断を Windows にゆだねます。</span><span class="sxs-lookup"><span data-stu-id="55a51-205">Instead, **SQLdiag** defers to Windows to determine whether a user has the appropriate rights to gather each requested diagnostic.</span></span>  
  
 <span data-ttu-id="55a51-206">**/G** が指定されていない場合、 **SQLdiag** は、ユーザーが Windows の **Administrators** グループのメンバーかどうかを判断するためのチェックを行い、ユーザーが [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Administrators **グループのメンバーではない場合は** の診断情報を収集しません。</span><span class="sxs-lookup"><span data-stu-id="55a51-206">If **/G** is not specified, **SQLdiag** checks to determine whether the user is a member of the Windows **Administrators** group, and will not collect [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] diagnostics if the user is not an **Administrators** group member.</span></span>  
  
 <span data-ttu-id="55a51-207">**/R**</span><span class="sxs-lookup"><span data-stu-id="55a51-207">**/R**</span></span>  
 <span data-ttu-id="55a51-208">**SQLdiag** をサービスとして登録します。</span><span class="sxs-lookup"><span data-stu-id="55a51-208">Registers **SQLdiag** as a service.</span></span> <span data-ttu-id="55a51-209">**SQLdiag** をサービスとして登録する場合に指定されるコマンド ライン引数は、後でサービスを実行するときのために維持されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-209">Any command line arguments that are specified when you register **SQLdiag** as a service are preserved for future runs of the service.</span></span>  
  
 <span data-ttu-id="55a51-210">**SQLdiag** がサービスとして登録されると、既定のサービス名は SQLDIAG となります。</span><span class="sxs-lookup"><span data-stu-id="55a51-210">When **SQLdiag** is registered as a service, the default service name is SQLDIAG.</span></span> <span data-ttu-id="55a51-211">既定のサービス名は **/A** 引数を使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="55a51-211">You can change the service name by using the **/A** argument.</span></span>  
  
 <span data-ttu-id="55a51-212">サービスを開始するには、次のとおり **START** コマンド ライン引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-212">Use the **START** command line argument to start the service:</span></span>  
  
 <span data-ttu-id="55a51-213">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="55a51-213">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="55a51-214">**net start** コマンドを次のように使用してサービスを開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="55a51-214">You can also use the **net start** command to start the service:</span></span>  
  
 <span data-ttu-id="55a51-215">**net start SQLDIAG**</span><span class="sxs-lookup"><span data-stu-id="55a51-215">**net start SQLDIAG**</span></span>  
  
 <span data-ttu-id="55a51-216">**/U**</span><span class="sxs-lookup"><span data-stu-id="55a51-216">**/U**</span></span>  
 <span data-ttu-id="55a51-217">**SQLdiag** のサービスとしての登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="55a51-217">Unregisters **SQLdiag** as a service.</span></span>  
  
 <span data-ttu-id="55a51-218">**/A** 引数を使用して、名前付きの **SQLdiag** インスタンスの登録を解除することもできます。</span><span class="sxs-lookup"><span data-stu-id="55a51-218">Use the **/A** argument also if unregistering a named **SQLdiag** instance.</span></span>  
  
 <span data-ttu-id="55a51-219">**/L**</span><span class="sxs-lookup"><span data-stu-id="55a51-219">**/L**</span></span>  
 <span data-ttu-id="55a51-220">**/B** 引数または **/E** 引数それぞれに、開始時刻または終了時刻も指定されている場合に、 **SQLdiag** を連続モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="55a51-220">Runs **SQLdiag** in continuous mode when a start time or end time is also specified with the **/B** or **/E** arguments, respectively.</span></span> <span data-ttu-id="55a51-221">**SQLdiag** は、定期的なシャットダウンによって診断情報の収集が停止した場合、自動的に再起動されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-221">**SQLdiag** automatically restarts after diagnostics collection stops due to a scheduled shutdown.</span></span> <span data-ttu-id="55a51-222">たとえば、 **/E** 引数または **/X** 引数で使用されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-222">For example, by using the **/E** or the **/X** arguments.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-223">**SQLdiag** は、 **/B** および **/E** コマンド ライン引数を使用して、開始時刻または終了時刻が指定されていない場合には、 **/L** 引数を無視します。</span><span class="sxs-lookup"><span data-stu-id="55a51-223">**SQLdiag** ignores the **/L** argument if a start time or end time is not specified by using the **/B** and **/E** command line arguments.</span></span>  
  
 <span data-ttu-id="55a51-224">**/L** を使用しても、暗黙にサービス モードになることはありません。</span><span class="sxs-lookup"><span data-stu-id="55a51-224">Using **/L** does not imply the service mode.</span></span> <span data-ttu-id="55a51-225">**SQLdiag** をサービスとして実行するときに **/L** を使用する場合は、サービスの登録時にコマンド ラインで指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-225">To use **/L** when running **SQLdiag** as a service, specify it on the command line when you register the service.</span></span>  
  
 <span data-ttu-id="55a51-226">**/X**</span><span class="sxs-lookup"><span data-stu-id="55a51-226">**/X**</span></span>  
 <span data-ttu-id="55a51-227">**SQLdiag** をスナップショット モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="55a51-227">Runs **SQLdiag** in snapshot mode.</span></span> <span data-ttu-id="55a51-228">**SQLdiag** は、構成したすべての診断情報のスナップショットを作成してから、自動的にシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="55a51-228">**SQLdiag** takes a snapshot of all configured diagnostics and then shuts down automatically.</span></span>  
  
 <span data-ttu-id="55a51-229">**START** | **STOP** | **STOP_ABORT**</span><span class="sxs-lookup"><span data-stu-id="55a51-229">**START** | **STOP** | **STOP_ABORT**</span></span>  
 <span data-ttu-id="55a51-230">**SQLdiag** サービスを開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="55a51-230">Starts or stops the **SQLdiag** service.</span></span> <span data-ttu-id="55a51-231">**STOP_ABORT** は、現在実行されている診断収集が終了していなくても、できるだけ早く強制的にサービスをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="55a51-231">**STOP_ABORT** forces the service to shut down as quickly as possible without finishing collection of diagnostics it is currently collecting.</span></span>  
  
 <span data-ttu-id="55a51-232">このサービス コントロール引数は、コマンド ラインで使用される最初の引数であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="55a51-232">When these service control arguments are used, they must be the first argument used on the command line.</span></span> <span data-ttu-id="55a51-233">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="55a51-233">For example:</span></span>  
  
 <span data-ttu-id="55a51-234">**SQLDIAG START**</span><span class="sxs-lookup"><span data-stu-id="55a51-234">**SQLDIAG START**</span></span>  
  
 <span data-ttu-id="55a51-235">**START** 、 **STOP**、または **STOP_ABORT**と共に使用し、 **SQLdiag**サービスの特定のインスタンスを制御できるのは、 **SQLdiag** の名前付きインスタンスを指定した **/A** 引数のみです。</span><span class="sxs-lookup"><span data-stu-id="55a51-235">Only the **/A** argument, which specifies a named instance of **SQLdiag**, can be used with **START**, **STOP**, or **STOP_ABORT** to control a specific instance of the **SQLdiag** service.</span></span> <span data-ttu-id="55a51-236">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="55a51-236">For example:</span></span>  
  
 <span data-ttu-id="55a51-237">**SQLDIAG START /A** _SQLdiag_application_name_</span><span class="sxs-lookup"><span data-stu-id="55a51-237">**SQLDIAG START /A** _SQLdiag_application_name_</span></span>  
  
## <a name="security-requirements"></a><span data-ttu-id="55a51-238">セキュリティ要件</span><span class="sxs-lookup"><span data-stu-id="55a51-238">Security Requirements</span></span>  
 <span data-ttu-id="55a51-239">**SQLdiag** を汎用モード ( **/G** コマンド ライン引数を指定) 以外のモードで実行する場合、**SQLdiag** を実行するユーザーは、Windows **Administrators** グループのメンバー、および [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sysadmin** 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="55a51-239">Unless **SQLdiag** is run in generic mode (by specifying the **/G** command line argument), the user who runs **SQLdiag** must be a member of the Windows **Administrators** group and a member of the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sysadmin** fixed server role.</span></span> <span data-ttu-id="55a51-240">既定では、 **SQLdiag** は Windows 認証を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] に接続しますが、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="55a51-240">By default, **SQLdiag** connects to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] by using Windows Authentication, but it also supports [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="55a51-241">パフォーマンスに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="55a51-241">Performance Considerations</span></span>  
 <span data-ttu-id="55a51-242">**SQLdiag** を実行した場合のパフォーマンスへの影響は、収集用に構成した診断データの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="55a51-242">The performance effects of running **SQLdiag** depend on the type of diagnostic data you have configured it to collect.</span></span> <span data-ttu-id="55a51-243">たとえば、 **のトレース情報を収集するように** SQLdiag [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を構成した場合、トレースを選択したイベント クラスの数に従ってサーバー パフォーマンスも影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="55a51-243">For example, if you have configured **SQLdiag** to collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] tracing information, the more event classes you choose to trace, the more your server performance is affected.</span></span>  
  
 <span data-ttu-id="55a51-244">**SQLdiag** の実行によるパフォーマンスへの影響は、構成した診断データを個別に収集する場合のコストの合計とほぼ同じになります。</span><span class="sxs-lookup"><span data-stu-id="55a51-244">The performance impact of running **SQLdiag** is approximately equivalent to the sum of the costs of collecting the configured diagnostics separately.</span></span> <span data-ttu-id="55a51-245">たとえば、 **SQLdiag** でトレースを収集すると、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]で収集した場合と同じパフォーマンス コストが生じます。</span><span class="sxs-lookup"><span data-stu-id="55a51-245">For example, collecting a trace with **SQLdiag** incurs the same performance cost as collecting it with [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="55a51-246">**SQLdiag** を使用した場合のパフォーマンスへの影響は無視しても問題ありません。</span><span class="sxs-lookup"><span data-stu-id="55a51-246">The performance impact of using **SQLdiag** is negligible.</span></span>  
  
## <a name="required-disk-space"></a><span data-ttu-id="55a51-247">必要なディスク領域</span><span class="sxs-lookup"><span data-stu-id="55a51-247">Required Disk Space</span></span>  
 <span data-ttu-id="55a51-248">**SQLdiag** ではさまざまな種類の診断情報を収集することができるため、 **SQLdiag** の実行に必要な空きディスク領域は、状況に応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="55a51-248">Because **SQLdiag** can collect different types of diagnostic information, the free disk space that is required to run **SQLdiag** varies.</span></span> <span data-ttu-id="55a51-249">収集される診断情報の量は、サーバーが処理している作業負荷の特性および量によって異なり、数 MB から数 GB までの範囲となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-249">The amount of diagnostic information collected depends on the nature and volume of the workload that the server is processing and may range from a few megabytes to several gigabytes.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="55a51-250">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="55a51-250">Configuration Files</span></span>  
 <span data-ttu-id="55a51-251">スタートアップ時に、 **SQLdiag** は構成ファイルおよび指定されたコマンド ライン引数を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="55a51-251">On startup, **SQLdiag** reads the configuration file and the command line arguments that have been specified.</span></span> <span data-ttu-id="55a51-252">**SQLdiag** が収集する診断情報の種類は、構成ファイルに指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-252">You specify the types of diagnostic information that **SQLdiag** collects in the configuration file.</span></span> <span data-ttu-id="55a51-253">既定では、 **SQLdiag** は **SQLdiag** ユーティリティ スタートアップ フォルダーにある SQLDiag.Xml 構成ファイルを使用します。この構成ファイルはツールが起動されるたびに抽出されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-253">By default, **SQLdiag** uses the SQLDiag.Xml configuration file, which is extracted each time the tool runs and is located in the **SQLdiag** utility startup folder.</span></span> <span data-ttu-id="55a51-254">構成ファイルでは、XML スキーマである SQLDiag_schema.xsd が使用されます。このスキーマ ファイルは、 **SQLdiag** を実行するたびに、実行可能ファイルからユーティリティ スタートアップ ディレクトリへ抽出されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-254">The configuration file uses the XML schema, SQLDiag_schema.xsd, which is also extracted into the utility startup directory from the executable file each time **SQLdiag** runs.</span></span>  
  
### <a name="editing-the-configuration-files"></a><span data-ttu-id="55a51-255">構成ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="55a51-255">Editing the Configuration Files</span></span>  
 <span data-ttu-id="55a51-256">SQLDiag.Xml のコピーや編集によって、 **SQLdiag** が収集する診断データの種類を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="55a51-256">You can copy and edit SQLDiag.Xml to change the types of diagnostic data that **SQLdiag** collects.</span></span> <span data-ttu-id="55a51-257">構成ファイルを編集する場合は必ず、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)]など、XML スキーマに対して構成ファイルを検証できる XML エディターを使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-257">When editing the configuration file always use an XML editor that can validate the configuration file against its XML schema, such as [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="55a51-258">SQLDiag.Xml は直接編集しないでください。</span><span class="sxs-lookup"><span data-stu-id="55a51-258">You should not edit SQLDiag.Xml directly.</span></span> <span data-ttu-id="55a51-259">代わりに、SQLDiag.Xml のコピーを作成し、同じフォルダーで新しいファイル名に変更します。</span><span class="sxs-lookup"><span data-stu-id="55a51-259">Instead, make a copy of SQLDiag.Xml and rename it to a new file name in the same folder.</span></span> <span data-ttu-id="55a51-260">次にその新規のファイルを編集し、 **/I** 引数を使用して **SQLdiag**に渡します。</span><span class="sxs-lookup"><span data-stu-id="55a51-260">Then edit the new file, and use the **/I** argument to pass it to **SQLdiag**.</span></span>  
  
#### <a name="editing-the-configuration-file-when-sqldiag-runs-as-a-service"></a><span data-ttu-id="55a51-261">SQLdiag をサービスとして実行する場合の構成ファイルの編集</span><span class="sxs-lookup"><span data-stu-id="55a51-261">Editing the Configuration File When SQLdiag Runs as a Service</span></span>  
 <span data-ttu-id="55a51-262">**SQLdiag** をサービスとして既に実行していて、構成ファイルを編集する必要がある場合は、 **/U** コマンド ライン引数を指定して SQLDIAG サービスの登録を解除します。次に、 **/R** コマンド ライン引数を使用してサービスを再登録します。</span><span class="sxs-lookup"><span data-stu-id="55a51-262">If you have already run **SQLdiag** as a service and need to edit the configuration file, unregister the SQLDIAG service by specifying the **/U** command line argument and then re-register the service by using the **/R** command line argument.</span></span> <span data-ttu-id="55a51-263">サービスの登録を解除、再登録すると、Windows レジストリにキャッシュされた古い構成情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-263">Unregistering and re-registering the service removes old configuration information that was cached in the Windows registry.</span></span>  
  
## <a name="output-folder"></a><span data-ttu-id="55a51-264">出力フォルダー</span><span class="sxs-lookup"><span data-stu-id="55a51-264">Output Folder</span></span>  
 <span data-ttu-id="55a51-265">出力フォルダーが **/O** 引数で指定されない場合、 **SQLdiag** は、 **SQLdiag** スタートアップ フォルダーの下に SQLDIAG という名前のサブフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="55a51-265">If you do not specify an output folder with the **/O** argument, **SQLdiag** creates a subfolder named SQLDIAG under the **SQLdiag** startup folder.</span></span> <span data-ttu-id="55a51-266">[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] など、大容量のトレースを伴う診断情報の収集を行う場合は、出力フォルダーが、要求される診断出力を格納するのに十分な空き領域を持つローカル ドライブにあることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="55a51-266">For diagnostic information collection that involves high volume tracing, such as [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] , make sure that the output folder is on a local drive with enough space to store the requested diagnostic output.</span></span>  
  
 <span data-ttu-id="55a51-267">**SQLdiag** を再起動すると、出力フォルダーの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="55a51-267">When **SQLdiag** is restarted, it overwrites the contents of the output folder.</span></span> <span data-ttu-id="55a51-268">上書きしない場合は、コマンド ラインで **/N 2** を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-268">To avoid this, specify **/N 2** on the command line.</span></span>  
  
## <a name="data-collection-process"></a><span data-ttu-id="55a51-269">データ収集プロセス</span><span class="sxs-lookup"><span data-stu-id="55a51-269">Data Collection Process</span></span>  
 <span data-ttu-id="55a51-270">**SQLdiag** を起動すると、SQLDiag.Xml で指定された診断情報を収集するための初期化チェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-270">When **SQLdiag** starts, it performs the initialization checks necessary to collect the diagnostic data that have been specified in SQLDiag.Xml.</span></span> <span data-ttu-id="55a51-271">このプロセスには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-271">This process may take several seconds.</span></span> <span data-ttu-id="55a51-272">コンソール アプリケーションとして実行した場合に **SQLdiag** が診断データの収集を開始すると、メッセージが表示されます。このメッセージは、 **SQLdiag** による収集が開始され、Ctrl キーを押しながら C キーを押すと停止できることを通知するものです。</span><span class="sxs-lookup"><span data-stu-id="55a51-272">After **SQLdiag** has started collecting diagnostic data when it is run as a console application, a message displays informing you that **SQLdiag** collection has started and that you can press CTRL+C to stop it.</span></span> <span data-ttu-id="55a51-273">**SQLdiag** がサービスとして実行されると、同様のメッセージが Windows イベント ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="55a51-273">When **SQLdiag** is run as a service, a similar message is written to the Windows event log.</span></span>  
  
 <span data-ttu-id="55a51-274">**SQLdiag** を使用して、再現可能な問題を診断する場合、このメッセージを受け取ってから、問題をサーバー上で再現する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-274">If you are using **SQLdiag** to diagnose a problem that you can reproduce, wait until you receive this message before you reproduce the problem on your server.</span></span>  
  
 <span data-ttu-id="55a51-275">**SQLdiag** は、多数の診断データを並行して収集します。</span><span class="sxs-lookup"><span data-stu-id="55a51-275">**SQLdiag** collects most diagnostic data in parallel.</span></span> <span data-ttu-id="55a51-276">情報が Windows パフォーマンス ログおよびイベント ログから収集される場合を除いて、すべての診断情報は、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sqlcmd** ユーティリティや Windows コマンド プロセッサなどのツールに接続することで収集されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-276">All diagnostic information is collected by connecting to tools, such as the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] **sqlcmd** utility or the Windows command processor, except when information is collected from Windows performance logs and event logs.</span></span> <span data-ttu-id="55a51-277">**SQLdiag** は、1 台のコンピューターにつき 1 つのワーカー スレッドを使用して、これらのツールによる診断データの収集を監視します。通常、複数のツールが終了するのを同時に待機します。</span><span class="sxs-lookup"><span data-stu-id="55a51-277">**SQLdiag** uses one worker thread per computer to monitor the diagnostic data collection of these other tools, often simultaneously waiting for several tools to complete.</span></span> <span data-ttu-id="55a51-278">収集プロセスの間、 **SQLdiag** は出力を各診断から出力フォルダーへルーティングします。</span><span class="sxs-lookup"><span data-stu-id="55a51-278">During the collection process, **SQLdiag** routes the output from each diagnostic to the output folder.</span></span>  
  
## <a name="stopping-data-collection"></a><span data-ttu-id="55a51-279">データ収集の停止</span><span class="sxs-lookup"><span data-stu-id="55a51-279">Stopping Data Collection</span></span>  
 <span data-ttu-id="55a51-280">**SQLdiag** が診断データの収集を開始した後は、これを停止するか、指定した時間に停止するように構成しない限り、データ収集は継続されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-280">After **SQLdiag** starts collecting diagnostic data, it continues to do so unless you stop it or it is configured to stop at a specified time.</span></span> <span data-ttu-id="55a51-281">**SQLdiag** が指定された時間に停止するように構成するには、停止時間の指定ができる **/E** 引数を使用するか、 **SQLdiag** をスナップショット モードで実行する **/X** 引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-281">You can configure **SQLdiag** to stop at a specified time by using the **/E** argument, which allows you to specify a stop time, or by using the **/X** argument, which causes **SQLdiag** to run in snapshot mode.</span></span>  
  
 <span data-ttu-id="55a51-282">**SQLdiag** が停止すると、開始されていたすべての診断情報が停止されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-282">When **SQLdiag** stops, it stops all diagnostics it has started.</span></span> <span data-ttu-id="55a51-283">たとえば、 [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] トレースの収集を停止すると、実行中の [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプトが停止され、データ収集中に発生したすべてのサブ プロセスも停止されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-283">For example, it stops [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] traces it was collecting, it stops executing [!INCLUDE[tsql](../includes/tsql-md.md)] scripts it was running, and it stops any sub processes it has spawned during data collection.</span></span> <span data-ttu-id="55a51-284">診断データの収集が完了した後で、 **SQLdiag** が終了します。</span><span class="sxs-lookup"><span data-stu-id="55a51-284">After diagnostic data collection has completed, **SQLdiag** exits.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-285">**SQLdiag** サービスの一時停止はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="55a51-285">Pausing the **SQLdiag** service is not supported.</span></span> <span data-ttu-id="55a51-286">**SQLdiag** サービスの一時停止を試行した場合は、一時停止したときに実行されている診断収集が完了してからサービスが停止されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-286">If you attempt to pause the **SQLdiag** service, it stops after it finishes collecting the diagnostics that it was collecting when you paused it.</span></span> <span data-ttu-id="55a51-287">停止した **SQLdiag** を再開すると、アプリケーションが再起動され、出力フォルダーが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="55a51-287">If you restart **SQLdiag** after stopping it, the application restarts and overwrites the output folder.</span></span> <span data-ttu-id="55a51-288">この出力フォルダーを上書きしない場合は、コマンド ラインで **/N 2** を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-288">To avoid overwriting the output folder, specify **/N 2** on the command line.</span></span>  
  
 <span data-ttu-id="55a51-289">**コンソール アプリケーションとしての実行時に SQLdiag を停止するには**</span><span class="sxs-lookup"><span data-stu-id="55a51-289">**To stop SQLdiag when running as a console application**</span></span>  
  
 <span data-ttu-id="55a51-290">**SQLdiag** をコンソール アプリケーションとして実行している場合、これを停止するには、 **SQLdiag** が実行されているコンソール ウィンドウで Ctrl キーを押しながら C キーを押します。</span><span class="sxs-lookup"><span data-stu-id="55a51-290">If you are running **SQLdiag** as a console application, press CTRL+C in the console window where **SQLdiag** is running to stop it.</span></span> <span data-ttu-id="55a51-291">Ctrl キーを押しながら C キーを押した後、コンソール ウィンドウにメッセージが表示され、 **SQLDiag** データ収集が終了したこと、およびプロセスがシャットダウンされるまで待機する必要があることが通知されます。プロセスのシャットダウンには数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-291">After you press CTRL+C, a message displays in the console window informing you that **SQLDiag** data collection is ending, and that you should wait until the process shuts down, which may take several minutes.</span></span>  
  
 <span data-ttu-id="55a51-292">2 度続けて、Ctrl キーを押しながら C キーを押すと、すべての子診断プロセスが停止し、アプリケーションが直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="55a51-292">Press Ctrl+C twice to terminate all child diagnostic processes and immediately terminate the application.</span></span>  
  
 <span data-ttu-id="55a51-293">**サービスとしての実行時に SQLdiag を停止するには**</span><span class="sxs-lookup"><span data-stu-id="55a51-293">**To stop SQLdiag when running as a service**</span></span>  
  
 <span data-ttu-id="55a51-294">**SQLdiag** をサービスとして実行する場合、 **SQLdiag** スタートアップ フォルダーの **SQLDiag STOP** を実行してサービスを停止します。</span><span class="sxs-lookup"><span data-stu-id="55a51-294">If you are running **SQLdiag** as a service, run **SQLDiag STOP** in the **SQLdiag** startup folder to stop it.</span></span>  
  
 <span data-ttu-id="55a51-295">同一のコンピューター上で **SQLdiag** のインスタンスを複数実行している場合、サービスを停止するときに、 **SQLdiag** インスタンス名をコマンド ラインに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="55a51-295">If you are running multiple instances of **SQLdiag** on the same computer, you can also pass the **SQLdiag** instance name to on the command line when you stop the service.</span></span> <span data-ttu-id="55a51-296">たとえば、Instance1 という名前の **SQLdiag** インスタンスを停止するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-296">For example, to stop a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG STOP /A Instance1  
```  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-297">**/A** は、 **START**、 **STOP**、または **STOP_ABORT**と共に使用できる唯一のコマンド ライン引数です。</span><span class="sxs-lookup"><span data-stu-id="55a51-297">**/A** is the only command-line argument that can be used with **START**, **STOP**, or **STOP_ABORT**.</span></span> <span data-ttu-id="55a51-298">**SQLdiag** の名前付きインスタンスをサービスのコントロール動詞のいずれかと共に指定する必要がある場合、上記の構文例に示したように、コマンド ラインでコントロール動詞の後に **/A** を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-298">If you need to specify a named instance of **SQLdiag** with one of the service control verbs, specify **/A** after the control verb on the command line as shown in the previous syntax example.</span></span> <span data-ttu-id="55a51-299">コントロール動詞を使用するときは、コマンド ラインの最初の引数であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="55a51-299">When control verbs are used, they must be the first argument on the command line.</span></span>  
  
 <span data-ttu-id="55a51-300">できるだけ早くサービスを停止するには、ユーティリティ スタートアップ フォルダーで **SQLDIAG STOP_ABORT** を実行します。</span><span class="sxs-lookup"><span data-stu-id="55a51-300">To stop the service as quickly as possible, run **SQLDIAG STOP_ABORT** in the utility startup folder.</span></span> <span data-ttu-id="55a51-301">このコマンドは、現在実行されている診断収集の終了を待たずに、収集を中断します。</span><span class="sxs-lookup"><span data-stu-id="55a51-301">This command aborts any diagnostics collecting currently being performed without waiting for them to finish.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-302">**SQLdiag** サービスを停止するには、 **SQLDiag STOP** または **SQLDIAG STOP_ABORT** を使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-302">Use **SQLDiag STOP** or **SQLDIAG STOP_ABORT** to stop the **SQLdiag** service.</span></span> <span data-ttu-id="55a51-303">**SQLdiag** またはその他の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービスを停止する場合は、Windows サービス コンソールを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="55a51-303">Do not use the Windows Services Console to stop **SQLdiag** or other [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] services.</span></span>  
  
## <a name="automatically-starting-and-stopping-sqldiag"></a><span data-ttu-id="55a51-304">SQLdiag の自動開始と停止</span><span class="sxs-lookup"><span data-stu-id="55a51-304">Automatically Starting and Stopping SQLdiag</span></span>  
 <span data-ttu-id="55a51-305">指定した時間に診断データ収集を自動的に開始および停止するには、 **/b**_start_time_と **/e**_stop_time_引数を24時間表記で使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-305">To automatically start and stop diagnostic data collection at a specified time, use the **/B**_start_time_ and **/E**_stop_time_ arguments, using 24-hour notation.</span></span> <span data-ttu-id="55a51-306">たとえば、ほぼ 02:00:00 に定期的に発生する問題のトラブルシューティングを行う場合、01:00 に診断データの収集を自動的に開始して、03:00:00 に自動的に終了するように **SQLdiag** を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="55a51-306">For example, if you are troubleshooting a problem that consistently appears at approximately 02:00:00, you can configure **SQLdiag** to automatically start collecting diagnostic data at 01:00 and automatically stop at 03:00:00.</span></span> <span data-ttu-id="55a51-307">開始時間および終了時間を指定するには、 **/B** 引数と **/E** 引数を使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-307">Use the **/B** and **/E** arguments to specify the start and stop time.</span></span> <span data-ttu-id="55a51-308">24 時間表記を使用して、YYYYMMDD_HH:MM:SS 形式で開始日時と終了日時を正確に指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-308">Use 24-hour notation to specify an exact start and stop date and time with the format YYYYMMDD_HH:MM:SS.</span></span> <span data-ttu-id="55a51-309">開始時間や終了時間を相対的に指定するには、次の例のように、開始時間および終了時間の前に **+** を付け、日付部分 (YYYYMMDD_) を省略します。次の例では、 **SQLdiag** は情報の収集を開始する前に 1 時間待機し、それから情報の収集を 3 時間行い、停止して終了します。</span><span class="sxs-lookup"><span data-stu-id="55a51-309">To specify a relative start or stop time, prefix the start and stop time with **+** and omit the date portion (YYYYMMDD_) as shown in the following example, which causes **SQLdiag** to wait 1 hour before it starts collecting information, then it collects information for 3 hours before it stops and exits:</span></span>  
  
```  
sqldiag /B +01:00:00 /E +03:00:00  
```  
  
 <span data-ttu-id="55a51-310">相対的な *start_time* が指定された場合、 **SQLdiag** は、現在の日時を基準とした相対的な時間に開始されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-310">When a relative *start_time* is specified, **SQLdiag** starts at a time that is relative to the current date and time.</span></span> <span data-ttu-id="55a51-311">相対的な *end_time* が指定された場合、 **SQLdiag** は、指定された *start_time*を基準とした相対的な時間に終了します。</span><span class="sxs-lookup"><span data-stu-id="55a51-311">When a relative *end_time* is specified, **SQLdiag** ends at a time that is relative to the specified *start_time*.</span></span> <span data-ttu-id="55a51-312">指定した開始日時または終了日時が過去の場合、 **SQLdiag** は開始日を未来の開始日時に強制的に変更します。</span><span class="sxs-lookup"><span data-stu-id="55a51-312">If the start or end date and time that you have specified is in the past, **SQLdiag** forcibly changes the start date so that the start date and time are in the future.</span></span>  
  
 <span data-ttu-id="55a51-313">これは、選択する開始日および終了日に対して重大な影響があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-313">This has important implications on the start and end dates you choose.</span></span> <span data-ttu-id="55a51-314">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="55a51-314">Consider the following example:</span></span>  
  
```  
sqldiag /B +01:00:00 /E 08:30:00  
```  
  
 <span data-ttu-id="55a51-315">現在の時間が 08:00 の場合、終了時間は、診断の収集が実際に開始される時間よりも過去の時間になってしまいます。</span><span class="sxs-lookup"><span data-stu-id="55a51-315">If the current time is 08:00, the end time passes before diagnostic collection actually begins.</span></span> <span data-ttu-id="55a51-316">指定した時間が過去となった場合、 **SQLDiag** は自動的に開始日および終了日を次の日に調整するため、この例では、診断収集は今日の 09:00 (相対開始時間が **+** で指定されている) に開始され、翌朝の 08:30 まで収集が継続されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-316">Because **SQLDiag** automatically adjusts start and end dates to the next day when they occur in the past, in this example diagnostic collection starts at 09:00 today (a relative start time has been specified with **+**) and continues collecting until 08:30 the following morning.</span></span>  
  
### <a name="stopping-and-restarting-sqldiag-to-collect-daily-diagnostics"></a><span data-ttu-id="55a51-317">診断を毎日収集するための SQLdiag の停止と再起動</span><span class="sxs-lookup"><span data-stu-id="55a51-317">Stopping and Restarting SQLdiag to Collect Daily Diagnostics</span></span>  
 <span data-ttu-id="55a51-318">**SQLdiag**を手動で開始および停止せずに、指定した診断のセットを毎日収集するには、 **/L** 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-318">To collect a specified set of diagnostics on a daily basis without having to manually start and stop **SQLdiag**, use the **/L** argument.</span></span> <span data-ttu-id="55a51-319">**/L** 引数により、定期的なシャットダウンの後で自動的に再起動されるため、 **SQLdiag** は継続的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-319">The **/L** argument causes **SQLdiag** to run continuously by automatically restarting itself after a scheduled shutdown.</span></span> <span data-ttu-id="55a51-320">**/L** が指定されている場合で、 **/E** 引数で指定された終了時間に到達したために **SQLdiag** 引数が停止する、または **/X** 引数を使用してスナップショット モードで実行されているために停止する場合、 **SQLdiag** は終了せずに再起動されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-320">When **/L** is specified, and **SQLdiag** stops because it has reached the end time specified with the **/E** argument, or it stops because it is being run in snapshot mode by using the **/X** argument, **SQLdiag** restarts instead of exiting.</span></span>  
  
 <span data-ttu-id="55a51-321">次の例では、 **SQLdiag** は継続モードで実行され、診断データの収集が 03:00:00 から 05:00:00 まで行われた後、自動的に再起動されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-321">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after diagnostic data collecting occurs between 03:00:00 and 05:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /E 05:00:00 /L  
```  
  
 <span data-ttu-id="55a51-322">次の例では、 **SQLdiag** は継続モードで実行され、診断データ スナップショットが 03:00:00 に作成された後、自動的に再起動されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-322">The following example specifies that **SQLdiag** run in continuous mode to automatically restart after taking a diagnostic data snapshot at 03:00:00.</span></span>  
  
```  
sqldiag /B 03:00:00 /X /L  
```  
  
## <a name="running-sqldiag-as-a-service"></a><span data-ttu-id="55a51-323">サービスとしての SQLdiag の実行</span><span class="sxs-lookup"><span data-stu-id="55a51-323">Running SQLdiag as a Service</span></span>  
 <span data-ttu-id="55a51-324">**SQLdiag** を使用して長期間にわたる診断データを収集するとき、その収集期間中に、 **SQLdiag** が実行されているコンピューターからログアウトしなければならない場合は、サービスとして実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-324">When you want to use **SQLdiag** to collect diagnostic data for long periods of time during which you might need to log out of the computer on which **SQLdiag** is running, you can run it as a service.</span></span>  
  
 <span data-ttu-id="55a51-325">**サービスとしての実行する SQLdiag を登録するには**</span><span class="sxs-lookup"><span data-stu-id="55a51-325">**To register SQLDiag to run as a service**</span></span>  
  
 <span data-ttu-id="55a51-326">**SQLdiag** を登録して、サービスとして実行するには、コマンド ラインで **/R** 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-326">You can register **SQLdiag** to run as a service by specifying the **/R** argument at the command line.</span></span> <span data-ttu-id="55a51-327">これにより、 **SQLdiag** が登録され、サービスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-327">This registers **SQLdiag** to run as a service.</span></span> <span data-ttu-id="55a51-328">**SQLdiag** サービス名は SQLDIAG です。</span><span class="sxs-lookup"><span data-stu-id="55a51-328">The **SQLdiag** service name is SQLDIAG.</span></span> <span data-ttu-id="55a51-329">**SQLDiag** をサービスとして登録するときにコマンド ラインに指定したその他の引数は維持され、サービスの開始時に再使用されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-329">Any other arguments you specify on the command line when you register **SQLDiag** as a service are preserved and reused when the service is started.</span></span>  
  
 <span data-ttu-id="55a51-330">既定の SQLDIAG サービス名を変更するには、 **/A** コマンド ライン引数を使用して、別の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-330">To change the default SQLDIAG service name, use the **/A** command-line argument to specify another name.</span></span> <span data-ttu-id="55a51-331">**SQLdiag** は **/A** で指定されたどの **SQLdiag** インスタンスにも、自動的にプレフィックスの DIAG$ を付け、わかりやすいサービス名を作成します。</span><span class="sxs-lookup"><span data-stu-id="55a51-331">**SQLdiag** automatically prefixes DIAG$ to any **SQLdiag** instance name specified with **/A** to create sensible service names.</span></span>  
  
 <span data-ttu-id="55a51-332">**SQLDIAG サービスの登録を解除するには**</span><span class="sxs-lookup"><span data-stu-id="55a51-332">**To unregister the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="55a51-333">サービスの登録を解除するには、 **/U** 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-333">To unregister the service, specify the **/U** argument.</span></span> <span data-ttu-id="55a51-334">サービスとしての **SQLdiag** の登録を解除すると、Windows サービスのレジストリ キーも削除されます。</span><span class="sxs-lookup"><span data-stu-id="55a51-334">Unregistering **SQLdiag** as a service also deletes the Windows registry keys of the service.</span></span>  
  
 <span data-ttu-id="55a51-335">**SQLDIAG サービスを開始または再起動するには**</span><span class="sxs-lookup"><span data-stu-id="55a51-335">**To start or restart the SQLDIAG service**</span></span>  
  
 <span data-ttu-id="55a51-336">SQLDIAG サービスを開始または再起動するには、コマンド ラインから **SQLDiag START** を実行します。</span><span class="sxs-lookup"><span data-stu-id="55a51-336">To start or restart the SQLDIAG service, run **SQLDiag START** from the command line.</span></span>  
  
 <span data-ttu-id="55a51-337">**/A** 引数を使用して、複数の **SQLdiag** インスタンスを実行する場合、サービスを開始するときに、コマンド ラインの **SQLdiag** インスタンス名を渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="55a51-337">If you are running multiple instances of **SQLdiag** by using the **/A** argument, you can also pass the **SQLdiag** instance name on the command line when you start the service.</span></span> <span data-ttu-id="55a51-338">たとえば、Instance1 という名前の **SQLdiag** インスタンスを開始するには、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="55a51-338">For example, to start a **SQLdiag** instance named Instance1, use the following syntax:</span></span>  
  
```  
SQLDIAG START /A Instance1  
```  
  
 <span data-ttu-id="55a51-339">**net start** コマンドを使用して SQLDIAG サービスを開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="55a51-339">You can also use the **net start** command to start the SQLDIAG service.</span></span>  
  
 <span data-ttu-id="55a51-340">**SQLdiag**を再起動すると、現在の出力フォルダーの内容が上書きされます。</span><span class="sxs-lookup"><span data-stu-id="55a51-340">When you restart **SQLdiag**, it overwrites the contents in the current output folder.</span></span> <span data-ttu-id="55a51-341">上書きしない場合は、コマンド ラインで **/N 2** を指定して、ユーティリティが起動するときに、出力フォルダーの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="55a51-341">To avoid this, specify **/N 2** on the command line to rename the output folder when the utility starts.</span></span>  
  
 <span data-ttu-id="55a51-342">**SQLdiag** サービスの一時停止はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="55a51-342">Pausing the **SQLdiag** service is not supported.</span></span>  
  
## <a name="running-multiple-instances-of-sqldiag"></a><span data-ttu-id="55a51-343">複数の SQLdiag インスタンスの実行</span><span class="sxs-lookup"><span data-stu-id="55a51-343">Running Multiple Instances of SQLdiag</span></span>  
 <span data-ttu-id="55a51-344">コマンドラインで **/a**_SQLdiag_application_name_を指定して、同じコンピューター上で複数の**SQLdiag**インスタンスを実行します。</span><span class="sxs-lookup"><span data-stu-id="55a51-344">Run multiple instances of **SQLdiag** on the same computer by specifying **/A**_SQLdiag_application_name_ on the command line.</span></span> <span data-ttu-id="55a51-345">これは、同一の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスから別の診断セットを同時に収集する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="55a51-345">This is useful for collecting different sets of diagnostics simultaneously from the same [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="55a51-346">たとえば、簡単なデータ収集を連続して実行するように、 **SQLdiag** の名前付きインスタンスを構成できます。</span><span class="sxs-lookup"><span data-stu-id="55a51-346">For example, you can configure a named instance of **SQLdiag** to continuously perform lightweight data collection.</span></span> <span data-ttu-id="55a51-347">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]で特定の問題が発生した場合は、既定の **SQLdiag** インスタンスを実行し、その問題に対する診断データを収集したり、 [!INCLUDE[msCoName](../includes/msconame-md.md)] カスタマー サポート サービスが収集を要望している問題に対する一連の診断データを収集したりできます。</span><span class="sxs-lookup"><span data-stu-id="55a51-347">Then, if a specific problem occurs on [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can run the default **SQLdiag** instance to collect diagnostics for that problem, or to gather a set of diagnostics that [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Support Services has asked you to gather to diagnose a problem.</span></span>  
  
## <a name="collecting-diagnostic-data-from-clustered-sql-server-instances"></a><span data-ttu-id="55a51-348">クラスター化された SQL Server インスタンスからの診断データの収集</span><span class="sxs-lookup"><span data-stu-id="55a51-348">Collecting Diagnostic Data from Clustered SQL Server Instances</span></span>  
 <span data-ttu-id="55a51-349">**SQLdiag** は、クラスター化された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスからの診断データの収集をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="55a51-349">**SQLdiag** supports collecting diagnostic data from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances.</span></span> <span data-ttu-id="55a51-350">クラスター化された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスから診断データを収集するには、構成ファイル SQLDiag.Xml 内にある **\<Machine>** 要素の **name** 属性に **"."** が指定されていることを確認してください。コマンド ラインで **/G** 引数は指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="55a51-350">To gather diagnostics from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, make sure that **"."** is specified for the **name** attribute of the **\<Machine>** element in the configuration file SQLDiag.Xml and do not specify the **/G** argument on the command line.</span></span> <span data-ttu-id="55a51-351">既定では、構成ファイル内の **name** 属性に対して **"."** が指定されていて、 **/G** 引数はオフになっています。</span><span class="sxs-lookup"><span data-stu-id="55a51-351">By default, **"."** is specified for the **name** attribute in the configuration file and the **/G** argument is turned off.</span></span> <span data-ttu-id="55a51-352">通常、クラスター化された [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスから収集する場合、構成ファイルの編集やコマンド ライン引数の変更は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="55a51-352">Typically, you do not need to edit the configuration file or change the command line arguments when collecting from a clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="55a51-353">**"."** がコンピューター名として指定されている場合、 **SQLdiag** はこのコンピューターがクラスター上で実行されていることを検出し、同時に、クラスター上にインストールされているすべての仮想 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] から診断情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="55a51-353">When **"."** is specified as the machine name, **SQLdiag** detects that it is running on a cluster, and simultaneously retrieves diagnostic information from all virtual instances of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that are installed on the cluster.</span></span> <span data-ttu-id="55a51-354">コンピューター上で実行されている [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つの仮想インスタンスのみから診断情報を収集する場合、SQLDiag.Xml 内の **\<Machine>** 要素の **name** 属性に対してその仮想 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を指定します。</span><span class="sxs-lookup"><span data-stu-id="55a51-354">If you want to collect diagnostic information from only one virtual instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that is running on a computer, specify that virtual [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] for the **name** attribute of the **\<Machine>** element in SQLDiag.Xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55a51-355">クラスター化された [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] インスタンスから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] トレース情報を収集するには、管理共有 (ADMIN$) をクラスター上で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55a51-355">To collect [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] trace information from clustered [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] instances, administrative shares (ADMIN$) must be enabled on the cluster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a51-356">参照</span><span class="sxs-lookup"><span data-stu-id="55a51-356">See Also</span></span>  
 [<span data-ttu-id="55a51-357">コマンド プロンプト ユーティリティ リファレンス &#40;データベース エンジン&#41;</span><span class="sxs-lookup"><span data-stu-id="55a51-357">Command Prompt Utility Reference &#40;Database Engine&#41;</span></span>](command-prompt-utility-reference-database-engine.md)  
  
  
