---
title: パッケージ実行ユーティリティ (DtExecUI) UI リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.dtexecui.general.f1
- sql12.dts.dtexecui.executionoptions.f1
- sql12.dts.dtexecui.configuration.f1
- sql12.dts.dtexecui.setvalues.f1
- sql12.dts.dtexecui.commandline.f1
- sql12.dts.dtexecui.commandfiles.f1
- sql12.dts.dtexecui.verification.f1
- sql12.dts.dtexecui.datasources.f1
- sql12.dts.dtexecui.reporting.f1
- sql12.dts.dtexecui.logging.f1
helpviewer_keywords:
- DTExecUI utility
ms.assetid: 3d71df39-126b-4c8e-bd77-128bbd5b0887
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 13601983a4ab841a2b64ff8e4fc722fcf5ae496c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642161"
---
# <a name="execute-package-utility-dtexecui-ui-reference"></a><span data-ttu-id="36d30-102">パッケージ実行ユーティリティ (DtExecUI) の UI リファレンス</span><span class="sxs-lookup"><span data-stu-id="36d30-102">Execute Package Utility (DtExecUI) UI Reference</span></span>
  <span data-ttu-id="36d30-103">**[パッケージ実行ユーティリティ]** を使用すると、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-103">Use the **Execute Package Utility** to run [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages.</span></span> <span data-ttu-id="36d30-104">このユーティリティは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース、[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストア、およびファイル システムの 3 つの場所のうちのいずれかに格納されているパッケージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-104">The utility runs packages that are stored in one of three locations: [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store, and the file system.</span></span> <span data-ttu-id="36d30-105">このユーザーインターフェイスで [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] は、 `dtexecui` **DTExec**コマンドプロンプトツールを使用してパッケージを実行する代わりに、またはコマンドプロンプトで「」と入力して開くことができます。</span><span class="sxs-lookup"><span data-stu-id="36d30-105">This user interface, which can be opened from [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or by typing `dtexecui` at a command prompt, is an alternative to running packages by using the **DTExec** command prompt tool.</span></span>  
  
 <span data-ttu-id="36d30-106">**dtexecui.exe** ユーティリティと同じ手順でパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-106">Packages execute in the same process as the **dtexecui.exe** utility.</span></span> <span data-ttu-id="36d30-107">このユーティリティは 32 ビット ツールであるため、64 ビット環境では Windows on Win32 (WOW) で実行される 64 ビット環境の **dtexecui.exe** を使用して、パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-107">Because this utility is a 32-bit tool, packages run by using **dtexecui.exe** in a 64-bit environment run in Windows on Win32 (WOW).</span></span> <span data-ttu-id="36d30-108">64 ビット コンピューターで dtexecui.exe ユーティリティを使用してコマンドを開発およびテストする場合、実稼働サーバー上でコマンドの配置またはスケジュール設定を行う前に、64 ビット バージョンの **dtexec.exe** を使用してコマンドのテストを 64 ビット モードで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="36d30-108">When developing and testing commands by using the dtexecui.exe utility on a 64-bit computer, you should test the commands in 64-bit mode by using the 64-bit version of **dtexec.exe** before deploying or scheduling the commands on a production server.</span></span>  
  
 <span data-ttu-id="36d30-109">**パッケージ実行ユーティリティ** は、 **DTExec** コマンド プロンプト ツールのグラフィカル ユーザー インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="36d30-109">The **Execute Package Utility** is a graphical user interface for the **DTExec** command prompt tool.</span></span> <span data-ttu-id="36d30-110">このユーザー インターフェイスにより、オプションの構成が容易になります。指定したオプションでパッケージを実行すると、 **DTExec** コマンド プロンプト ツールに渡されるコマンド ラインが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-110">The user interface makes it easy to configure options and it automatically assembles the command line that is passed to the **DTExec** command prompt tool when you run the package from the specified options.</span></span>  
  
 <span data-ttu-id="36d30-111">**パッケージ実行ユーティリティ** は、 **DTExec** を直接実行するときに使用するコマンド ラインの作成にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-111">The **Execute Package Utility** can also be used to assemble command lines that you use when running **DTExec** directly.</span></span>  
  
### <a name="to-open-execute-package-utility-in-sql-server-management-studio"></a><span data-ttu-id="36d30-112">SQL Server Management Studio でパッケージ実行ユーティリティを開くには</span><span class="sxs-lookup"><span data-stu-id="36d30-112">To open Execute Package Utility in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="36d30-113">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[オブジェクト エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36d30-113">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **View** menu, click **Object Explorer**.</span></span>  
  
2.  <span data-ttu-id="36d30-114">オブジェクト エクスプローラーで **[接続]** をクリックし、 **[Integration Services]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36d30-114">In Object Explorer, click **Connect**, and then click **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="36d30-115">**[サーバーへの接続]** ダイアログ ボックスで、 **[サーバー名]** ボックスにサーバー名を入力し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36d30-115">In the **Connect to Server** dialog box, enter the server name in the **Server name** list, and then click **Connect**.</span></span>  
  
4.  <span data-ttu-id="36d30-116">**[格納されたパッケージ]** フォルダーとサブフォルダーを展開し、実行するパッケージを右クリックして **[パッケージの実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36d30-116">Expand the **Stored Package**s folder and subfolders, right-click the package you want to run, and then click **Run Package**.</span></span>  
  
### <a name="to-open-the-execute-package-utility-at-the-command-prompt"></a><span data-ttu-id="36d30-117">コマンド プロンプトでパッケージ実行ユーティリティを開くには</span><span class="sxs-lookup"><span data-stu-id="36d30-117">To open the Execute Package Utility at the Command Prompt</span></span>  
  
-   <span data-ttu-id="36d30-118">コマンド プロンプト ウィンドウで、`dtexecui` を実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-118">In a command prompt window, run `dtexecui`.</span></span>  
  
 <span data-ttu-id="36d30-119">ここでは、 **[パッケージ実行ユーティリティ]** ダイアログ ボックスのページについて説明します。</span><span class="sxs-lookup"><span data-stu-id="36d30-119">The following sections describe pages of the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="general-page"></a><span data-ttu-id="36d30-120">[全般] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-120">General Page</span></span>  
 <span data-ttu-id="36d30-121">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[全般]** ページを使用すると、パッケージの名前と場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-121">Use the **General** page of the **Execute Package Utility** dialog box to specify a package name and location.</span></span>  
  
 <span data-ttu-id="36d30-122">パッケージがリモート サーバーに保存されている場合でも、パッケージ実行ユーティリティ (dtexecui.exe) は常にローカル コンピューターでパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-122">The Execute Package utility (dtexecui.exe) always runs a package on the local computer, even if the package is saved on a remote server.</span></span> <span data-ttu-id="36d30-123">リモート パッケージがリモート サーバーに保存されている構成ファイルを使用する場合は、パッケージ実行ユーティリティが構成を見つけられない可能性があり、この場合はパッケージは失敗します。</span><span class="sxs-lookup"><span data-stu-id="36d30-123">If the remote package uses configuration files that also are saved on the remote server, then the Execute Package utility may not locate the configurations and the package fails.</span></span> <span data-ttu-id="36d30-124">この問題を回避するには、 \\\myserver\myfile のような汎用名前付け規則 (UNC) 共有名を使用して、構成を参照するようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="36d30-124">To avoid this problem, the configurations must be referenced by using a Universal Naming Convention (UNC) share name like \\\myserver\myfile.</span></span>  
  
### <a name="static-options"></a><span data-ttu-id="36d30-125">静的オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-125">Static Options</span></span>  
 <span data-ttu-id="36d30-126">**[パッケージ ソース]**</span><span class="sxs-lookup"><span data-stu-id="36d30-126">**Package source**</span></span>  
 <span data-ttu-id="36d30-127">以下のオプションを使用して、パッケージを実行する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-127">Specify the location of the package to run, using the following options:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="36d30-128">値</span><span class="sxs-lookup"><span data-stu-id="36d30-128">Value</span></span>|<span data-ttu-id="36d30-129">説明</span><span class="sxs-lookup"><span data-stu-id="36d30-129">Description</span></span>|  
|<span data-ttu-id="36d30-130">**SQL Server**</span><span class="sxs-lookup"><span data-stu-id="36d30-130">**SQL Server**</span></span>|<span data-ttu-id="36d30-131">パッケージが [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に存在する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-131">Select this option when the package resides in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="36d30-132">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証に使用するユーザー名とパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-132">Specify an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and provide a user name and password for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="36d30-133">各ユーザー名とパスワードによって、 **/USER** _ユーザー名_ および **/PASSWORD** _パスワード_ オプションがコマンド プロンプトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-133">Each user name and password adds the **/USER** _username_ and **/PASSWORD** _password_ options to the command prompt.</span></span>|  
|<span data-ttu-id="36d30-134">**ファイル システム**</span><span class="sxs-lookup"><span data-stu-id="36d30-134">**File system**</span></span>|<span data-ttu-id="36d30-135">パッケージがファイル システムに存在する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-135">Select this option when the package resides in the file system.</span></span>|  
|<span data-ttu-id="36d30-136">**[SSIS パッケージ ストア]**</span><span class="sxs-lookup"><span data-stu-id="36d30-136">**SSIS Package Store**</span></span>|<span data-ttu-id="36d30-137">パッケージが [!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ ストアに存在する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-137">Select this option when the package resides in the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Package Store.</span></span>|  
  
 <span data-ttu-id="36d30-138">これらの各選択には以下のオプションのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="36d30-138">Each of these selections has the following set of options.</span></span>  
  
 <span data-ttu-id="36d30-139">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-139">**Execute**</span></span>  
 <span data-ttu-id="36d30-140">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-140">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-141">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-141">**Close**</span></span>  
 <span data-ttu-id="36d30-142">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-142">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
### <a name="dynamic-options"></a><span data-ttu-id="36d30-143">動的オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-143">Dynamic Options</span></span>  
  
#### <a name="package-source--sql-server"></a><span data-ttu-id="36d30-144">[パッケージ ソース] = [SQL Server]</span><span class="sxs-lookup"><span data-stu-id="36d30-144">Package Source = SQL Server</span></span>  
 <span data-ttu-id="36d30-145">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="36d30-145">**Server**</span></span>  
 <span data-ttu-id="36d30-146">パッケージが存在する場所のサーバーの名前を入力するか、一覧からサーバーを選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-146">Type the name of the server where the package resides, or select a server from the list.</span></span>  
  
 <span data-ttu-id="36d30-147">**[サーバー ログオン]**</span><span class="sxs-lookup"><span data-stu-id="36d30-147">**Log on to the server**</span></span>  
 <span data-ttu-id="36d30-148">パッケージが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続するために、Windows 認証と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証のどちらを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-148">Specify whether the package should use Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="36d30-149">より高いセキュリティのためには Windows 認証をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="36d30-149">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="36d30-150">Windows 認証ではユーザー名とパスワードを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="36d30-150">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="36d30-151">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-151">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="36d30-152">Windows 認証と [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ユーザー アカウントを使用してログオンします。</span><span class="sxs-lookup"><span data-stu-id="36d30-152">Select this option to use Windows Authentication and log on using a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows user account.</span></span>  
  
 <span data-ttu-id="36d30-153">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-153">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="36d30-154">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="36d30-154">Select this option to use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication.</span></span> <span data-ttu-id="36d30-155">指定されたログイン名とパスワードを使用して、信頼関係の低い接続から接続した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン アカウントが設定されているかどうか、指定されたパスワードが以前に記録されたパスワードと一致しているかどうかを確認することで認証を行います。</span><span class="sxs-lookup"><span data-stu-id="36d30-155">When a user connects with a specified login name and password from a non-trusted connection, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] performs the authentication by checking to see if a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login account has been set up and if the specified password matches the one previously recorded.</span></span> <span data-ttu-id="36d30-156">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン アカウントが見つからない場合、認証は失敗し、エラー メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-156">If [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cannot find the login account, authentication fails, and the user receives an error message.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="36d30-157">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="36d30-157">When possible, use Windows Authentication.</span></span>  
  
 <span data-ttu-id="36d30-158">**Package**</span><span class="sxs-lookup"><span data-stu-id="36d30-158">**Package**</span></span>  
 <span data-ttu-id="36d30-159">パッケージ名を入力するか、参照ボタン ( **[...]** ) をクリックし **[SSIS パッケージの選択]** ダイアログ ボックスを使用してパッケージを検索します。</span><span class="sxs-lookup"><span data-stu-id="36d30-159">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
#### <a name="package-source--file-system"></a><span data-ttu-id="36d30-160">[パッケージ ソース] = [ファイル システム]</span><span class="sxs-lookup"><span data-stu-id="36d30-160">Package Source = File System</span></span>  
 <span data-ttu-id="36d30-161">**Package**</span><span class="sxs-lookup"><span data-stu-id="36d30-161">**Package**</span></span>  
 <span data-ttu-id="36d30-162">パッケージ名を入力するか、参照ボタン ( **[...]** ) をクリックし [開く] ダイアログ ボックスを使用してパッケージを検索します。</span><span class="sxs-lookup"><span data-stu-id="36d30-162">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the Open dialog box.</span></span> <span data-ttu-id="36d30-163">既定では、.dtsx 拡張子を持つファイルのみがダイアログ ボックスに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-163">By default, the dialog box lists only files that have the .dtsx extension.</span></span>  
  
#### <a name="package-source--ssis-package-store"></a><span data-ttu-id="36d30-164">[パッケージ ソース] = [SSIS パッケージ ストア]</span><span class="sxs-lookup"><span data-stu-id="36d30-164">Package Source = SSIS Package Store</span></span>  
 <span data-ttu-id="36d30-165">**[サーバー]**</span><span class="sxs-lookup"><span data-stu-id="36d30-165">**Server**</span></span>  
 <span data-ttu-id="36d30-166">パッケージが存在する場所のコンピューターの名前を入力するか、一覧からコンピューターを選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-166">Type the name of the computer where the package resides, or select a computer from the list.</span></span>  
  
 <span data-ttu-id="36d30-167">**[サーバー ログオン]**</span><span class="sxs-lookup"><span data-stu-id="36d30-167">**Log on to the server**</span></span>  
 <span data-ttu-id="36d30-168">パッケージが Microsoft Windows 認証を使用して、パッケージ ソースに接続するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-168">Specify whether the package should use Microsoft Windows Authentication to connect to the package source.</span></span> <span data-ttu-id="36d30-169">より高いセキュリティのためには Windows 認証をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="36d30-169">Windows Authentication is recommended for better security.</span></span> <span data-ttu-id="36d30-170">Windows 認証ではユーザー名とパスワードを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="36d30-170">With Windows Authentication you do not have to specify a user name and password.</span></span>  
  
 <span data-ttu-id="36d30-171">**[Windows 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-171">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="36d30-172">Windows 認証と Microsoft Windows ユーザー アカウントを使用してログオンします。</span><span class="sxs-lookup"><span data-stu-id="36d30-172">Select this option to use Windows Authentication and log on using a Microsoft Windows user account.</span></span>  
  
 <span data-ttu-id="36d30-173">**[SQL Server 認証を使用する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-173">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="36d30-174">**[SSIS パッケージ ストア]** に格納されているパッケージを実行する場合は、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="36d30-174">This option is not available when you run a package stored in the **SSIS Package Store**.</span></span>  
  
 <span data-ttu-id="36d30-175">**Package**</span><span class="sxs-lookup"><span data-stu-id="36d30-175">**Package**</span></span>  
 <span data-ttu-id="36d30-176">パッケージ名を入力するか、参照ボタン ( **[...]** ) をクリックし **[SSIS パッケージの選択]** ダイアログ ボックスを使用してパッケージを検索します。</span><span class="sxs-lookup"><span data-stu-id="36d30-176">Type the name of the package, or click the ellipsis button **(...)** to locate a package using the **Select an SSIS Package** dialog box.</span></span>  
  
## <a name="configurations-page"></a><span data-ttu-id="36d30-177">[構成] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-177">Configurations Page</span></span>  
 <span data-ttu-id="36d30-178">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[構成]** ページを使用すると、実行時に読み込む構成ファイルの選択と、読み込む順序の指定ができます。</span><span class="sxs-lookup"><span data-stu-id="36d30-178">Use the **Configurations** page of the **Execute Package Utility** dialog box to select the configuration files to load at run time, and to specify the order in which they load.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-179">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-179">Options</span></span>  
 <span data-ttu-id="36d30-180">**[構成ファイル]**</span><span class="sxs-lookup"><span data-stu-id="36d30-180">**Configuration files**</span></span>  
 <span data-ttu-id="36d30-181">パッケージが使用する構成を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-181">Lists the configurations that the package uses.</span></span> <span data-ttu-id="36d30-182">構成ファイルごとに、 **/CONFIGFILE filename** オプションがコマンド プロンプトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-182">Each configuration file adds a **/CONFIGFILE filename** option to the command prompt.</span></span>  
  
 <span data-ttu-id="36d30-183">**方向キー**</span><span class="sxs-lookup"><span data-stu-id="36d30-183">**Arrow keys**</span></span>  
 <span data-ttu-id="36d30-184">一覧で構成ファイルを選択し、右側にある方向キーを使用して読み込み順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="36d30-184">Select a configuration file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="36d30-185">構成は、一覧の一番上から順に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="36d30-185">Configurations load in order starting from the top of the list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="36d30-186">複数の構成によって同じプロパティが修正される場合、最後に読み込まれる構成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-186">If multiple configurations modify the same property, the configuration that loads last is used.</span></span>  
  
 <span data-ttu-id="36d30-187">**追加**</span><span class="sxs-lookup"><span data-stu-id="36d30-187">**Add**</span></span>  
 <span data-ttu-id="36d30-188">**[開く]** ダイアログ ボックスを使用して、構成を追加します。</span><span class="sxs-lookup"><span data-stu-id="36d30-188">Click to add configurations using the **Open** dialog box.</span></span> <span data-ttu-id="36d30-189">既定では、.dtsconfig 拡張子を持つファイルのみがダイアログ ボックスに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-189">By default, the dialog box lists only files that have the .dtsconfig extension.</span></span>  
  
 <span data-ttu-id="36d30-190">**Remove**</span><span class="sxs-lookup"><span data-stu-id="36d30-190">**Remove**</span></span>  
 <span data-ttu-id="36d30-191">一覧で構成を選択し、次に **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="36d30-191">Select a configuration file in the list and then click **Remove**.</span></span>  
  
 <span data-ttu-id="36d30-192">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-192">**Execute**</span></span>  
 <span data-ttu-id="36d30-193">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-193">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-194">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-194">**Close**</span></span>  
 <span data-ttu-id="36d30-195">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-195">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-files-page"></a><span data-ttu-id="36d30-196">[コマンド ファイル] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-196">Command Files Page</span></span>  
 <span data-ttu-id="36d30-197">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[コマンド ファイル]** ページを使用すると、実行時に読み込むコマンド ファイルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-197">Use the **Command Files** page of the **Execute Package Utility** dialog box to select the command files to load at run time.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-198">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-198">Options</span></span>  
 <span data-ttu-id="36d30-199">**[コマンド ファイル]**</span><span class="sxs-lookup"><span data-stu-id="36d30-199">**Command files**</span></span>  
 <span data-ttu-id="36d30-200">パッケージが使用するコマンド ファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-200">Lists the command files that the package uses.</span></span> <span data-ttu-id="36d30-201">パッケージは、複数のファイルを使用してコマンド ライン オプションを設定できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-201">A package can use multiple files to set command-line options.</span></span>  
  
 <span data-ttu-id="36d30-202">**方向キー**</span><span class="sxs-lookup"><span data-stu-id="36d30-202">**Arrow keys**</span></span>  
 <span data-ttu-id="36d30-203">一覧でコマンド ファイルを選択し、右側にある方向キーを使用して読み込み順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="36d30-203">Select a command file in the list, and use the arrow keys at right to change the loading order.</span></span> <span data-ttu-id="36d30-204">コマンド ファイルは、一覧の一番上から順に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="36d30-204">Command files load in order, starting from the top of the list.</span></span>  
  
 <span data-ttu-id="36d30-205">**追加**</span><span class="sxs-lookup"><span data-stu-id="36d30-205">**Add**</span></span>  
 <span data-ttu-id="36d30-206">**[開く]** ダイアログ ボックスを使用して、コマンド ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="36d30-206">Click to add a command file, using the **Open** dialog box.</span></span>  
  
 <span data-ttu-id="36d30-207">**Remove**</span><span class="sxs-lookup"><span data-stu-id="36d30-207">**Remove**</span></span>  
 <span data-ttu-id="36d30-208">テキスト ボックスでコマンド ファイルを選択し、 **[削除]** ボタンを使用して削除します。</span><span class="sxs-lookup"><span data-stu-id="36d30-208">Select a command file in the text box, and then remove it using the **Remove** button.</span></span>  
  
 <span data-ttu-id="36d30-209">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-209">**Execute**</span></span>  
 <span data-ttu-id="36d30-210">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-210">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-211">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-211">**Close**</span></span>  
 <span data-ttu-id="36d30-212">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-212">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="connection-managers-page"></a><span data-ttu-id="36d30-213">[接続マネージャー] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-213">Connection Managers Page</span></span>  
 <span data-ttu-id="36d30-214">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、パッケージで使用する接続マネージャーの接続文字列を編集できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-214">Use the **Connection Managers** page of the **Execute Package Utility** dialog box to edit the connection strings of the connection managers that the package uses.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-215">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-215">Options</span></span>  
 <span data-ttu-id="36d30-216">**接続マネージャー**</span><span class="sxs-lookup"><span data-stu-id="36d30-216">**Connection Manager**</span></span>  
 <span data-ttu-id="36d30-217">チェック ボックスをオンにすると、 **[接続文字列]** 列が編集可能になります。</span><span class="sxs-lookup"><span data-stu-id="36d30-217">Select its check box to make the **Connection String** column editable.</span></span>  
  
 <span data-ttu-id="36d30-218">**説明**</span><span class="sxs-lookup"><span data-stu-id="36d30-218">**Description**</span></span>  
 <span data-ttu-id="36d30-219">それぞれの接続マネージャーの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-219">View a description for each connection manager.</span></span> <span data-ttu-id="36d30-220">説明は編集できません。</span><span class="sxs-lookup"><span data-stu-id="36d30-220">Descriptions cannot be edited.</span></span>  
  
 <span data-ttu-id="36d30-221">**接続文字列**</span><span class="sxs-lookup"><span data-stu-id="36d30-221">**Connection String**</span></span>  
 <span data-ttu-id="36d30-222">接続マネージャーの接続文字列を編集します。</span><span class="sxs-lookup"><span data-stu-id="36d30-222">Edit the connection string for a connection manager.</span></span> <span data-ttu-id="36d30-223">このフィールドは、 **[接続マネージャー]** チェック ボックスがオンの場合にのみ編集できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-223">This field is editable only when the **Connection Manager** check box is selected.</span></span>  
  
 <span data-ttu-id="36d30-224">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-224">**Execute**</span></span>  
 <span data-ttu-id="36d30-225">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-225">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-226">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-226">**Close**</span></span>  
 <span data-ttu-id="36d30-227">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-227">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="execution-options-page"></a><span data-ttu-id="36d30-228">[実行オプション] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-228">Execution Options Page</span></span>  
 <span data-ttu-id="36d30-229">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[実行オプション]** ページを使用すると、パッケージの実行時オプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-229">Use the **Execution Options** page of the **Execute Package Utility** dialog box to specify run-time options for the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-230">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-230">Options</span></span>  
 <span data-ttu-id="36d30-231">**[検証時に警告が発生したらパッケージを失敗とする]**</span><span class="sxs-lookup"><span data-stu-id="36d30-231">**Fail package on validation warnings**</span></span>  
 <span data-ttu-id="36d30-232">検証時に警告が発生した場合に、パッケージを失敗させるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-232">Indicate whether the package fails if a validation warning occurs.</span></span>  
  
 <span data-ttu-id="36d30-233">**[パッケージを実行せずに検証する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-233">**Validate package without executing**</span></span>  
 <span data-ttu-id="36d30-234">パッケージの検証のみを行うかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-234">Indicate whether the package is validated only.</span></span>  
  
 <span data-ttu-id="36d30-235">**[同時実行するファイルの最大数]**</span><span class="sxs-lookup"><span data-stu-id="36d30-235">**Maximum concurrent executables**</span></span>  
 <span data-ttu-id="36d30-236">パッケージで同時に実行できる実行可能ファイルの最大数を指定するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-236">Indicate whether you want to specify the maximum number of executables that can run in the package at the same time.</span></span> <span data-ttu-id="36d30-237">このチェック ボックスをオンにして、スピン ボックスで実行可能ファイルの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-237">After you select this check box, use the spin box to specify the maximum number of executables.</span></span>  
  
 <span data-ttu-id="36d30-238">**[パッケージのチェックポイントを有効にする]**</span><span class="sxs-lookup"><span data-stu-id="36d30-238">**Enable package checkpoints**</span></span>  
 <span data-ttu-id="36d30-239">パッケージのチェックポイントを有効にするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-239">Indicate whether to enable package checkpoints.</span></span>  
  
 <span data-ttu-id="36d30-240">**[チェックポイント ファイル]**</span><span class="sxs-lookup"><span data-stu-id="36d30-240">**Checkpoint file**</span></span>  
 <span data-ttu-id="36d30-241">パッケージのチェックポイントが有効な場合、使用されるパッケージのチェックポイント ファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-241">List the checkpoint file the package uses, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="36d30-242">**[参照]**</span><span class="sxs-lookup"><span data-stu-id="36d30-242">**Browse**</span></span>  
 <span data-ttu-id="36d30-243">パッケージのチェックポイントが有効な場合、参照ボタン ( **[...]** ) をクリックし、 **[開く]** ダイアログ ボックスを使用してチェックポイント ファイルを探します。</span><span class="sxs-lookup"><span data-stu-id="36d30-243">Click the browse button **(...)** to locate the checkpoint file using the **Open** dialog box, if you enable package checkpoints.</span></span> <span data-ttu-id="36d30-244">チェックポイント ファイルが既に指定されている場合、選択したファイルで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="36d30-244">If a checkpoint file is already specified, it is replaced by the selected file.</span></span>  
  
 <span data-ttu-id="36d30-245">**[再開オプションをオーバーライドする]**</span><span class="sxs-lookup"><span data-stu-id="36d30-245">**Override restart options**</span></span>  
 <span data-ttu-id="36d30-246">パッケージのチェックポイントが有効な場合、再開オプションをオーバーライドするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-246">Indicate whether to override restart options, if you enable package checkpoints.</span></span>  
  
 <span data-ttu-id="36d30-247">**[再開オプション]**</span><span class="sxs-lookup"><span data-stu-id="36d30-247">**Restart option**</span></span>  
 <span data-ttu-id="36d30-248">再開オプションをオーバーライドする場合、チェックポイントの使用方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-248">Select how to use checkpoints, if you override restart options.</span></span>  
  
 <span data-ttu-id="36d30-249">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-249">**Execute**</span></span>  
 <span data-ttu-id="36d30-250">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-250">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-251">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-251">**Close**</span></span>  
 <span data-ttu-id="36d30-252">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-252">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="reporting-page"></a><span data-ttu-id="36d30-253">[レポート] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-253">Reporting Page</span></span>  
 <span data-ttu-id="36d30-254">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[レポート]** ページを使用すると、パッケージを実行したときにコンソールのログに記録する、イベントとパッケージに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-254">Use the **Reporting** page of the **Execute Package Utility** dialog box to specify the events and information about the package to log to the console when the package runs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-255">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-255">Options</span></span>  
 <span data-ttu-id="36d30-256">**[コンソールのイベント]**</span><span class="sxs-lookup"><span data-stu-id="36d30-256">**Console events**</span></span>  
 <span data-ttu-id="36d30-257">レポートに記録するイベントとメッセージの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-257">Indicate the events and types of messages to report.</span></span>  
  
 <span data-ttu-id="36d30-258">**なし**</span><span class="sxs-lookup"><span data-stu-id="36d30-258">**None**</span></span>  
 <span data-ttu-id="36d30-259">レポートを作成しない場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-259">Select for no reporting.</span></span>  
  
 <span data-ttu-id="36d30-260">**エラー**</span><span class="sxs-lookup"><span data-stu-id="36d30-260">**Errors**</span></span>  
 <span data-ttu-id="36d30-261">エラー メッセージをレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-261">Select to report error messages.</span></span>  
  
 <span data-ttu-id="36d30-262">**Warnings**</span><span class="sxs-lookup"><span data-stu-id="36d30-262">**Warnings**</span></span>  
 <span data-ttu-id="36d30-263">警告メッセージをレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-263">Select to report warning messages.</span></span>  
  
 <span data-ttu-id="36d30-264">**[カスタム イベント]**</span><span class="sxs-lookup"><span data-stu-id="36d30-264">**Custom Events**</span></span>  
 <span data-ttu-id="36d30-265">カスタム イベントのメッセージをレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-265">Select to report custom event messages.</span></span>  
  
 <span data-ttu-id="36d30-266">**[パイプライン イベント]**</span><span class="sxs-lookup"><span data-stu-id="36d30-266">**Pipeline Events**</span></span>  
 <span data-ttu-id="36d30-267">データ フロー イベントのメッセージをレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-267">Select to report data flow events messages.</span></span>  
  
 <span data-ttu-id="36d30-268">**情報**</span><span class="sxs-lookup"><span data-stu-id="36d30-268">**Information**</span></span>  
 <span data-ttu-id="36d30-269">情報メッセージをレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-269">Select to report information messages.</span></span>  
  
 <span data-ttu-id="36d30-270">**詳細**</span><span class="sxs-lookup"><span data-stu-id="36d30-270">**Verbose**</span></span>  
 <span data-ttu-id="36d30-271">詳細レポートを使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-271">Select to use verbose reporting.</span></span>  
  
 <span data-ttu-id="36d30-272">**[コンソールのログ記録]**</span><span class="sxs-lookup"><span data-stu-id="36d30-272">**Console logging**</span></span>  
 <span data-ttu-id="36d30-273">選択したイベントが発生したときにログに書き込まれる情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-273">Specify the information that you want written to the log when the selected event occurs.</span></span>  
  
 <span data-ttu-id="36d30-274">**Name**</span><span class="sxs-lookup"><span data-stu-id="36d30-274">**Name**</span></span>  
 <span data-ttu-id="36d30-275">パッケージを作成した人物の名前をレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-275">Select to report the name of the person who created the package.</span></span>  
  
 <span data-ttu-id="36d30-276">**コンピューター**</span><span class="sxs-lookup"><span data-stu-id="36d30-276">**Computer**</span></span>  
 <span data-ttu-id="36d30-277">パッケージが実行されるコンピューターの名前をレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-277">Select to report the name of the computer the package is running on.</span></span>  
  
 <span data-ttu-id="36d30-278">**[オペレーター]**</span><span class="sxs-lookup"><span data-stu-id="36d30-278">**Operator**</span></span>  
 <span data-ttu-id="36d30-279">パッケージを起動した人物の名前をレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-279">Select to report the name of the person who started the package.</span></span>  
  
 <span data-ttu-id="36d30-280">**ソース名**</span><span class="sxs-lookup"><span data-stu-id="36d30-280">**Source name**</span></span>  
 <span data-ttu-id="36d30-281">パッケージの名前をレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-281">Select to report the package name.</span></span>  
  
 <span data-ttu-id="36d30-282">**[ソース GUID]**</span><span class="sxs-lookup"><span data-stu-id="36d30-282">**Source GUID**</span></span>  
 <span data-ttu-id="36d30-283">パッケージの GUID をレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-283">Select to report the package GUID.</span></span>  
  
 <span data-ttu-id="36d30-284">**[実行 GUID]**</span><span class="sxs-lookup"><span data-stu-id="36d30-284">**Execution GUID**</span></span>  
 <span data-ttu-id="36d30-285">パッケージ実行インスタンスの GUID をレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-285">Select to report the GUID of the package execution instance.</span></span>  
  
 <span data-ttu-id="36d30-286">**メッセージ**</span><span class="sxs-lookup"><span data-stu-id="36d30-286">**Message**</span></span>  
 <span data-ttu-id="36d30-287">メッセージをレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-287">Select to report messages.</span></span>  
  
 <span data-ttu-id="36d30-288">**[開始時刻および終了時刻]**</span><span class="sxs-lookup"><span data-stu-id="36d30-288">**Start time and end time**</span></span>  
 <span data-ttu-id="36d30-289">パッケージの開始時刻と終了時刻をレポートに記録する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-289">Select to report when the package began and finished.</span></span>  
  
 <span data-ttu-id="36d30-290">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-290">**Execute**</span></span>  
 <span data-ttu-id="36d30-291">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-291">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-292">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-292">**Close**</span></span>  
 <span data-ttu-id="36d30-293">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-293">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="logging-page"></a><span data-ttu-id="36d30-294">[ログ記録] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-294">Logging Page</span></span>  
 <span data-ttu-id="36d30-295">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[ログ記録]** ページを使用すると、ログ プロバイダーの実行時にパッケージを利用できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-295">Use the **Logging** page of the **Execute Package Utility** dialog box to make log providers available to the package at run time.</span></span> <span data-ttu-id="36d30-296">パッケージのログ プロバイダーの種類とログに接続するための接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-296">Provide the package log provider type and the connection string for connecting to the log.</span></span> <span data-ttu-id="36d30-297">ログ プロバイダーのエントリごとに、 **/LOGGER**_classid_ オプションがコマンド プロンプトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-297">Each log provider entry adds a **/LOGGER**_classid_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-298">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-298">Options</span></span>  
 <span data-ttu-id="36d30-299">**[ログ プロバイダー]**</span><span class="sxs-lookup"><span data-stu-id="36d30-299">**Log Provider**</span></span>  
 <span data-ttu-id="36d30-300">一覧からログ プロバイダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="36d30-300">Select a log provider from the list.</span></span>  
  
 <span data-ttu-id="36d30-301">**[構成文字列]**</span><span class="sxs-lookup"><span data-stu-id="36d30-301">**Configuration String**</span></span>  
 <span data-ttu-id="36d30-302">ログの場所を指すパッケージから接続マネージャーの名前を選択するか、ログ プロバイダーに接続するための接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="36d30-302">Select the name of the connection manager from the package that points to the log location, or type the connection string for connecting to the log provider.</span></span>  
  
 <span data-ttu-id="36d30-303">**Remove**</span><span class="sxs-lookup"><span data-stu-id="36d30-303">**Remove**</span></span>  
 <span data-ttu-id="36d30-304">ログ プロバイダーを選択し、クリックして削除します。</span><span class="sxs-lookup"><span data-stu-id="36d30-304">Select a log provider and click to remove it.</span></span>  
  
 <span data-ttu-id="36d30-305">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-305">**Execute**</span></span>  
 <span data-ttu-id="36d30-306">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-306">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-307">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-307">**Close**</span></span>  
 <span data-ttu-id="36d30-308">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-308">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="set-values-page"></a><span data-ttu-id="36d30-309">[値の設定] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-309">Set Values Page</span></span>  
 <span data-ttu-id="36d30-310">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[値の設定]** ページを使用すると、プロパティのパスと値を入力することにより、パッケージ、実行可能ファイル、接続、変数、およびログ プロバイダーのプロパティ値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-310">Use the **Set Values** page of the **Execute Package Utility** dialog box to set the property values of packages, executables, connections, variables, and log providers by typing the paths of properties and the property values.</span></span> <span data-ttu-id="36d30-311">パスのエントリごとに、コマンド プロンプトに **/SET**_propertypath;value_ オプションが追加されます。</span><span class="sxs-lookup"><span data-stu-id="36d30-311">Each path entry adds a **/SET**_propertypath;value_ option to the command prompt.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-312">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-312">Options</span></span>  
 <span data-ttu-id="36d30-313">**[プロパティのパス]**</span><span class="sxs-lookup"><span data-stu-id="36d30-313">**Property Path**</span></span>  
 <span data-ttu-id="36d30-314">プロパティのパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="36d30-314">Type the path of the property.</span></span> <span data-ttu-id="36d30-315">パスの構文では、円記号 (\\) を使用して続くアイテムがコンテナーであることを示し、ピリオド (.) を使用して続くアイテムがプロパティであることを示します。また、角かっこはコレクションのメンバーを示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-315">The path syntax uses a backslash (\\) to indicate that the following item is a container, the period (.) to indicate the following item is a property, and brackets to indicate a collection member.</span></span> <span data-ttu-id="36d30-316">メンバーは、インデックスまたは名前で識別できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-316">The member can be identified by its index or its name.</span></span> <span data-ttu-id="36d30-317">たとえば、パッケージ変数のプロパティのパスは、「\Package.Variables[MyVariable].Value」です。</span><span class="sxs-lookup"><span data-stu-id="36d30-317">For example, the property path of a package variable is \Package.Variables[MyVariable].Value.</span></span>  
  
 <span data-ttu-id="36d30-318">**Value**</span><span class="sxs-lookup"><span data-stu-id="36d30-318">**Value**</span></span>  
 <span data-ttu-id="36d30-319">プロパティの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="36d30-319">Type the value of the property.</span></span>  
  
 <span data-ttu-id="36d30-320">**Remove**</span><span class="sxs-lookup"><span data-stu-id="36d30-320">**Remove**</span></span>  
 <span data-ttu-id="36d30-321">プロパティのパスを選択し、クリックして削除します。</span><span class="sxs-lookup"><span data-stu-id="36d30-321">Select a property path and click to remove it.</span></span>  
  
 <span data-ttu-id="36d30-322">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-322">**Execute**</span></span>  
 <span data-ttu-id="36d30-323">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-323">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-324">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-324">**Close**</span></span>  
 <span data-ttu-id="36d30-325">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-325">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="verification-page"></a><span data-ttu-id="36d30-326">[検証] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-326">Verification Page</span></span>  
 <span data-ttu-id="36d30-327">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[検証]** ページを使用すると、パッケージを検証するための条件を設定できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-327">Use the **Verification** page of the **Execute Package** dialog box to set criteria for verifying the package.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-328">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-328">Options</span></span>  
 <span data-ttu-id="36d30-329">**[署名付きパッケージのみ実行する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-329">**Execute only signed packages**</span></span>  
 <span data-ttu-id="36d30-330">署名されたパッケージのみ実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-330">Select to execute only packages that have been signed.</span></span>  
  
 <span data-ttu-id="36d30-331">**[パッケージのビルドを検証する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-331">**Verify package build**</span></span>  
 <span data-ttu-id="36d30-332">パッケージのビルドを検証します。</span><span class="sxs-lookup"><span data-stu-id="36d30-332">Select to verify the package build.</span></span>  
  
 <span data-ttu-id="36d30-333">Build</span><span class="sxs-lookup"><span data-stu-id="36d30-333">Build</span></span>  
 <span data-ttu-id="36d30-334">ビルドに関連付けられた連続するビルド番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-334">Specify the sequential Build number associated with the build.</span></span>  
  
 <span data-ttu-id="36d30-335">**[パッケージ ID を確認する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-335">**Verify package ID**</span></span>  
 <span data-ttu-id="36d30-336">パッケージ ID を確認します。</span><span class="sxs-lookup"><span data-stu-id="36d30-336">Select to verify the package ID.</span></span>  
  
 <span data-ttu-id="36d30-337">[パッケージ ID]</span><span class="sxs-lookup"><span data-stu-id="36d30-337">Package ID</span></span>  
 <span data-ttu-id="36d30-338">パッケージの識別番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-338">Specify the package identification number.</span></span>  
  
 <span data-ttu-id="36d30-339">**[バージョン ID を確認する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-339">**Verify version ID**</span></span>  
 <span data-ttu-id="36d30-340">バージョン ID を確認します。</span><span class="sxs-lookup"><span data-stu-id="36d30-340">Select to verify the version ID.</span></span>  
  
 <span data-ttu-id="36d30-341">バージョン ID</span><span class="sxs-lookup"><span data-stu-id="36d30-341">Version ID</span></span>  
 <span data-ttu-id="36d30-342">バージョンの識別番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="36d30-342">Specify the version identification number.</span></span>  
  
 <span data-ttu-id="36d30-343">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-343">**Execute**</span></span>  
 <span data-ttu-id="36d30-344">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-344">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-345">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-345">**Close**</span></span>  
 <span data-ttu-id="36d30-346">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-346">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="command-line-page"></a><span data-ttu-id="36d30-347">[コマンド ライン] ページ</span><span class="sxs-lookup"><span data-stu-id="36d30-347">Command Line Page</span></span>  
 <span data-ttu-id="36d30-348">**[パッケージ実行ユーティリティ]** ダイアログ ボックスの **[コマンド ライン]** ノードを使用すると、さまざまなダイアログ ボックスで作成されたオプションを使用して生成されたコマンド ラインを編集できます。</span><span class="sxs-lookup"><span data-stu-id="36d30-348">Use the **Command Line** node of the **Execute Package Utility** dialog box to edit the command line that has been generated by the options created by the various dialogs.</span></span>  
  
### <a name="options"></a><span data-ttu-id="36d30-349">オプション</span><span class="sxs-lookup"><span data-stu-id="36d30-349">Options</span></span>  
 <span data-ttu-id="36d30-350">**[元のオプションを復元する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-350">**Restore the original options**</span></span>  
 <span data-ttu-id="36d30-351">コマンド ラインを元の状態に復元します。</span><span class="sxs-lookup"><span data-stu-id="36d30-351">Click to restore the command line to its original state.</span></span> <span data-ttu-id="36d30-352">**[コマンド ラインを手動で編集する]** オプションを使用して変更してから、元のコマンド ライン オプションを復元する場合は、このオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="36d30-352">Use this option if you have made modifications using the **Edit the command line manually** option and want to restore the original command-line options.</span></span>  
  
 <span data-ttu-id="36d30-353">**[コマンド ラインを手動で編集する]**</span><span class="sxs-lookup"><span data-stu-id="36d30-353">**Edit the command line manually**</span></span>  
 <span data-ttu-id="36d30-354">**[コマンド ライン]** テキスト ボックスのコマンド ラインを編集します。</span><span class="sxs-lookup"><span data-stu-id="36d30-354">Click to edit the command line in the **Command line** text box.</span></span>  
  
 <span data-ttu-id="36d30-355">**コマンド ライン**</span><span class="sxs-lookup"><span data-stu-id="36d30-355">**Command line**</span></span>  
 <span data-ttu-id="36d30-356">現在のコマンド ラインを表示します。</span><span class="sxs-lookup"><span data-stu-id="36d30-356">Displays the current command line.</span></span> <span data-ttu-id="36d30-357">コマンド ラインを手動で編集するためにこのオプションを選択した場合に編集可能です。</span><span class="sxs-lookup"><span data-stu-id="36d30-357">Editable if you selected the option to edit the command line manually.</span></span>  
  
 <span data-ttu-id="36d30-358">**実行**</span><span class="sxs-lookup"><span data-stu-id="36d30-358">**Execute**</span></span>  
 <span data-ttu-id="36d30-359">パッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="36d30-359">Click to run the package.</span></span>  
  
 <span data-ttu-id="36d30-360">**[閉じる]**</span><span class="sxs-lookup"><span data-stu-id="36d30-360">**Close**</span></span>  
 <span data-ttu-id="36d30-361">**[パッケージ実行ユーティリティ]** ダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="36d30-361">Click to close the **Execute Package Utility** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d30-362">参照</span><span class="sxs-lookup"><span data-stu-id="36d30-362">See Also</span></span>  
 [<span data-ttu-id="36d30-363">dtexec ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="36d30-363">dtexec Utility</span></span>](dtexec-utility.md)  
  
  
