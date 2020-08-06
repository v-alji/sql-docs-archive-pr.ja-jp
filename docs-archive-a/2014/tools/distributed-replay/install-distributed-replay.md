---
title: コマンドプロンプトから分散再生をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: be7c950b886356c08050e37825d5215b62aeb8cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640283"
---
# <a name="install-distributed-replay-from-the-command-prompt"></a><span data-ttu-id="47084-102">コマンド プロンプトからの 分散再生のインストール</span><span class="sxs-lookup"><span data-stu-id="47084-102">Install Distributed Replay from the Command Prompt</span></span>
  <span data-ttu-id="47084-103">分散再生の新しいインスタンスをコマンド プロンプトでインストールすると、インストールする機能とその機能の構成を指定できます。</span><span class="sxs-lookup"><span data-stu-id="47084-103">Installing a new instance of Distributed Replay at the command prompt enables you to specify the features to install and how they should be configured.</span></span> <span data-ttu-id="47084-104">コマンド プロンプトによるインストールでは、分散再生ユーティリティ コンポーネントのインストール、修復、アップグレード、およびアンインストールがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="47084-104">The command prompt installation supports installing, repairing, upgrading, and uninstalling of the Distributed Replay components.</span></span> <span data-ttu-id="47084-105">コマンド プロンプトを使用してインストールする場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、/Q パラメーターを使用した Full Quiet モードがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="47084-105">When installing through the command prompt, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports full quiet mode by using the /Q parameter.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="47084-106">ローカル インストールの場合は、セットアップを管理者として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47084-106">For local installations, you must run Setup as an administrator.</span></span> <span data-ttu-id="47084-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をリモート共有からインストールする場合は、そのリモート共有に対する読み取り権限と実行権限を持つドメイン アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47084-107">If you install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] from a remote share, you must use a domain account that has read and execute permissions on the remote share.</span></span>  
  
## <a name="installation-parameters"></a><span data-ttu-id="47084-108">インストール パラメーター</span><span class="sxs-lookup"><span data-stu-id="47084-108">Installation Parameters</span></span>  
 <span data-ttu-id="47084-109">最上位の機能には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]、ツールなどがあります。</span><span class="sxs-lookup"><span data-stu-id="47084-109">The list of top-level features include [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], and Tools.</span></span> <span data-ttu-id="47084-110">ツール機能により、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理ツール、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブック、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]、およびその他の共有コンポーネントがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="47084-110">The Tools feature will install [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Tools, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online, [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and other shared components.</span></span> <span data-ttu-id="47084-111">分散再生コンポーネントをインストールするには、次のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="47084-111">To install the Distributed Replay components, specify the following parameters:</span></span>  
  
|<span data-ttu-id="47084-112">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="47084-112">Component</span></span>|<span data-ttu-id="47084-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47084-113">Parameter</span></span>|  
|---------------|---------------|  
|<span data-ttu-id="47084-114">[分散再生コントローラー]</span><span class="sxs-lookup"><span data-stu-id="47084-114">Distributed Replay controller</span></span>|<span data-ttu-id="47084-115">**DREPLAY_CTLR**</span><span class="sxs-lookup"><span data-stu-id="47084-115">**DREPLAY_CTLR**</span></span>|  
|<span data-ttu-id="47084-116">[分散再生クライアント]</span><span class="sxs-lookup"><span data-stu-id="47084-116">Distributed Replay client</span></span>|<span data-ttu-id="47084-117">**DREPLAY_CLT**</span><span class="sxs-lookup"><span data-stu-id="47084-117">**DREPLAY_CLT**</span></span>|  
|<span data-ttu-id="47084-118">管理ツール</span><span class="sxs-lookup"><span data-stu-id="47084-118">Administration Tool</span></span>|<span data-ttu-id="47084-119">**ツール**</span><span class="sxs-lookup"><span data-stu-id="47084-119">**Tools**</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="47084-120">分散再生をインストールした後、コントローラー コンピューターとクライアント コンピューターのファイアウォール ルールを作成し、ターゲット サーバー上で各クライアント コンピューターの権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47084-120">After you install Distributed Replay you must create firewall rules on the controller and client computers, and grant each client computer permissions on the target server.</span></span> <span data-ttu-id="47084-121">詳細については、「 [インストール後の手順の実行](complete-the-post-installation-steps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47084-121">For more information, see [Complete the Post-Installation Steps](complete-the-post-installation-steps.md).</span></span>  
  
 <span data-ttu-id="47084-122">次の表に示すパラメーターは、インストール用のコマンド ライン スクリプトを作成する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="47084-122">Use the parameters in the following table to develop command line scripts for installation.</span></span>  
  
|<span data-ttu-id="47084-123">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47084-123">Parameter</span></span>|<span data-ttu-id="47084-124">説明</span><span class="sxs-lookup"><span data-stu-id="47084-124">Description</span></span>|<span data-ttu-id="47084-125">サポートされる値</span><span class="sxs-lookup"><span data-stu-id="47084-125">Supported Values</span></span>|  
|---------------|-----------------|----------------------|  
|<span data-ttu-id="47084-126">/CTLRSVCACCOUNT</span><span class="sxs-lookup"><span data-stu-id="47084-126">/CTLRSVCACCOUNT</span></span><br /><br /> <span data-ttu-id="47084-127">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-127">**Optional**</span></span>|<span data-ttu-id="47084-128">分散再生コントローラー サービスのサービス アカウント。</span><span class="sxs-lookup"><span data-stu-id="47084-128">Service account for the Distributed Replay controller service.</span></span>|<span data-ttu-id="47084-129">アカウントとパスワードのチェック</span><span class="sxs-lookup"><span data-stu-id="47084-129">Checks account and password</span></span>|  
|<span data-ttu-id="47084-130">/CTLRSVCPASSWORD</span><span class="sxs-lookup"><span data-stu-id="47084-130">/CTLRSVCPASSWORD</span></span><br /><br /> <span data-ttu-id="47084-131">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-131">**Optional**</span></span>|<span data-ttu-id="47084-132">分散再生コントローラー のサービス アカウントのパスワード。</span><span class="sxs-lookup"><span data-stu-id="47084-132">Password for the Distributed Replay controller service account.</span></span>|<span data-ttu-id="47084-133">アカウントとパスワードのチェック</span><span class="sxs-lookup"><span data-stu-id="47084-133">Checks account and password</span></span>|  
|<span data-ttu-id="47084-134">/CTLRSTARTUPTYPE</span><span class="sxs-lookup"><span data-stu-id="47084-134">/CTLRSTARTUPTYPE</span></span><br /><br /> <span data-ttu-id="47084-135">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-135">**Optional**</span></span>|<span data-ttu-id="47084-136">分散再生コントローラー サービスのスタートアップの種類。</span><span class="sxs-lookup"><span data-stu-id="47084-136">Startup type for the Distributed Replay controller service.</span></span>|<span data-ttu-id="47084-137">自動</span><span class="sxs-lookup"><span data-stu-id="47084-137">Automatic</span></span><br /><br /> <span data-ttu-id="47084-138">無効</span><span class="sxs-lookup"><span data-stu-id="47084-138">Disabled</span></span><br /><br /> <span data-ttu-id="47084-139">マニュアル</span><span class="sxs-lookup"><span data-stu-id="47084-139">Manual</span></span>|  
|<span data-ttu-id="47084-140">/CTLRUSERS</span><span class="sxs-lookup"><span data-stu-id="47084-140">/CTLRUSERS</span></span><br /><br /> <span data-ttu-id="47084-141">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-141">**Optional**</span></span>|<span data-ttu-id="47084-142">分散再生コントローラー サービスの権限を持つユーザーを指定します。</span><span class="sxs-lookup"><span data-stu-id="47084-142">Specify which users have permissions for the Distributed Replay controller service.</span></span>|<span data-ttu-id="47084-143">区切り記号に " " (スペース) を使用した、一連のユーザー アカウント文字列</span><span class="sxs-lookup"><span data-stu-id="47084-143">Set of user account strings using " " (space) for delimiter</span></span><br /><br /> <span data-ttu-id="47084-144">**重要**:分散再生コントローラー サービスを構成するとき、分散再生クライアント サービスの実行に使用する 1 つまたは複数のユーザー アカウントを指定できます。</span><span class="sxs-lookup"><span data-stu-id="47084-144">**Important**: When you configure the Distributed Replay controller service, you can specify one or more user accounts that will be used to run the Distributed Replay client services.</span></span> <span data-ttu-id="47084-145">サポートされているアカウントの一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="47084-145">The following is the list of supported accounts:</span></span><br /><br /> <span data-ttu-id="47084-146">ドメイン ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="47084-146">Domain user account</span></span><br /><br /> <span data-ttu-id="47084-147">ユーザーによって作成されたローカル ユーザー アカウント</span><span class="sxs-lookup"><span data-stu-id="47084-147">User created local user account</span></span><br /><br /> <span data-ttu-id="47084-148">管理者</span><span class="sxs-lookup"><span data-stu-id="47084-148">Administrator</span></span><br /><br /> <span data-ttu-id="47084-149">仮想アカウントおよび管理されたサービス アカウント (MSA)</span><span class="sxs-lookup"><span data-stu-id="47084-149">Virtual account and MSA (Managed Service Account)</span></span><br /><br /> <span data-ttu-id="47084-150">ネットワーク サービス、ローカル サービス、およびシステム</span><span class="sxs-lookup"><span data-stu-id="47084-150">Network Services, Local Services, and System</span></span><br /><br /> <br /><br /> <span data-ttu-id="47084-151">グループ アカウント (ローカルまたはドメイン) およびその他の組み込みのアカウント (Everyone など) は使用できません。</span><span class="sxs-lookup"><span data-stu-id="47084-151">Group accounts (local or domain) and other built-in accounts (like Everyone) are not accepted.</span></span>|  
|<span data-ttu-id="47084-152">/CLTSVCACCOUNT</span><span class="sxs-lookup"><span data-stu-id="47084-152">/CLTSVCACCOUNT</span></span><br /><br /> <span data-ttu-id="47084-153">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-153">**Optional**</span></span>|<span data-ttu-id="47084-154">分散再生クライアント サービスのサービス アカウント。</span><span class="sxs-lookup"><span data-stu-id="47084-154">Service account for the Distributed Replay client service.</span></span>|<span data-ttu-id="47084-155">アカウントとパスワードのチェック</span><span class="sxs-lookup"><span data-stu-id="47084-155">Checks account and password</span></span>|  
|<span data-ttu-id="47084-156">/CLTSVCPASSWORD</span><span class="sxs-lookup"><span data-stu-id="47084-156">/CLTSVCPASSWORD</span></span><br /><br /> <span data-ttu-id="47084-157">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-157">**Optional**</span></span>|<span data-ttu-id="47084-158">分散再生クライアント のサービス アカウントのパスワード。</span><span class="sxs-lookup"><span data-stu-id="47084-158">Password for the Distributed Replay client service account.</span></span>|<span data-ttu-id="47084-159">アカウントとパスワードのチェック</span><span class="sxs-lookup"><span data-stu-id="47084-159">Checks account and password</span></span>|  
|<span data-ttu-id="47084-160">/CLTSTARTUPTYPE</span><span class="sxs-lookup"><span data-stu-id="47084-160">/CLTSTARTUPTYPE</span></span><br /><br /> <span data-ttu-id="47084-161">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-161">**Optional**</span></span>|<span data-ttu-id="47084-162">分散再生クライアント サービスのスタートアップの種類。</span><span class="sxs-lookup"><span data-stu-id="47084-162">Startup type for the Distributed Replay client service.</span></span>|<span data-ttu-id="47084-163">自動</span><span class="sxs-lookup"><span data-stu-id="47084-163">Automatic</span></span><br /><br /> <span data-ttu-id="47084-164">無効</span><span class="sxs-lookup"><span data-stu-id="47084-164">Disabled</span></span><br /><br /> <span data-ttu-id="47084-165">マニュアル</span><span class="sxs-lookup"><span data-stu-id="47084-165">Manual</span></span>|  
|<span data-ttu-id="47084-166">/CLTCTLRNAME</span><span class="sxs-lookup"><span data-stu-id="47084-166">/CLTCTLRNAME</span></span><br /><br /> <span data-ttu-id="47084-167">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-167">**Optional**</span></span>|<span data-ttu-id="47084-168">分散再生クライアント サービスと通信するクライアントのコンピューター名です。</span><span class="sxs-lookup"><span data-stu-id="47084-168">The computer name that the client communicates with for the Distributed Replay Controller service.</span></span>||  
|<span data-ttu-id="47084-169">/CLTWORKINGDIR</span><span class="sxs-lookup"><span data-stu-id="47084-169">/CLTWORKINGDIR</span></span><br /><br /> <span data-ttu-id="47084-170">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-170">**Optional**</span></span>|<span data-ttu-id="47084-171">分散再生クライアント サービス用の作業ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="47084-171">The working directory for the Distributed Replay Client service.</span></span>|<span data-ttu-id="47084-172">有効なパス</span><span class="sxs-lookup"><span data-stu-id="47084-172">Valid path</span></span>|  
|<span data-ttu-id="47084-173">/CLTRESULTDIR</span><span class="sxs-lookup"><span data-stu-id="47084-173">/CLTRESULTDIR</span></span><br /><br /> <span data-ttu-id="47084-174">**省略可能**</span><span class="sxs-lookup"><span data-stu-id="47084-174">**Optional**</span></span>|<span data-ttu-id="47084-175">分散再生クライアント サービス用の結果ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="47084-175">The result directory for the Distributed Replay Client service.</span></span>|<span data-ttu-id="47084-176">有効なパス</span><span class="sxs-lookup"><span data-stu-id="47084-176">Valid path</span></span>|  
  
### <a name="sample-syntax"></a><span data-ttu-id="47084-177">サンプル構文:</span><span class="sxs-lookup"><span data-stu-id="47084-177">Sample Syntax:</span></span>  
 <span data-ttu-id="47084-178">**分散再生コントローラー コンポーネントをインストールする場合**</span><span class="sxs-lookup"><span data-stu-id="47084-178">**To install the Distributed Replay controller component**</span></span>  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 <span data-ttu-id="47084-179">**分散再生クライアント コンポーネントをインストールする場合**</span><span class="sxs-lookup"><span data-stu-id="47084-179">**To install the Distributed Replay client component**</span></span>  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  