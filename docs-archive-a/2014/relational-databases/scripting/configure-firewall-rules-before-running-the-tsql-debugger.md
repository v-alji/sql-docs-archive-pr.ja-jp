---
title: Transact-SQL デバッガーの構成
ms.custom: seo-lt-2019
ms.date: 10/20/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.error.sqlde_register_failed
- vs.debug.error.sqlde_accessdenied
- vs.debug.error.sqlde_firewall.remotemachines
helpviewer_keywords:
- Transact-SQL debugger, remote connections
- Windows Firewall [Database Engine], Transact-SQL debugger
- Transact-SQL debugger, Windows Firewall
- Transact-SQL debugger, configuring
- ports [SQL Server], Transact-SQL debugger
- TCP/IP [SQL Server], port numbers
ms.assetid: f50e0b0d-eaf0-4f4a-be83-96f5be63e7ea
author: rothja
ms.author: jroth
ms.openlocfilehash: a320e77e86c933a33d96d708580d5050b0c06de2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643774"
---
# <a name="configure-the-transact-sql-debugger"></a><span data-ttu-id="7b96e-102">Transact-SQL デバッガーの構成</span><span class="sxs-lookup"><span data-stu-id="7b96e-102">Configure the Transact-SQL Debugger</span></span>
  <span data-ttu-id="7b96e-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] クエリ エディターとは別のコンピューター上で動作する [!INCLUDE[ssDE](../../includes/ssde-md.md)] インスタンスに接続するときに [!INCLUDE[ssDE](../../includes/ssde-md.md)] デバッグを有効にするように Windows ファイアウォール規則を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-103">Windows Firewall rules must be configured to enable [!INCLUDE[tsql](../../includes/tsql-md.md)] debugging when connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] that is running on a different computer than the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span>  
  
## <a name="configuring-the-transact-sql-debugger"></a><span data-ttu-id="7b96e-104">Transact-SQL デバッガーの構成</span><span class="sxs-lookup"><span data-stu-id="7b96e-104">Configuring the Transact-SQL Debugger</span></span>  
 <span data-ttu-id="7b96e-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーには、サーバー側のコンポーネントとクライアント側のコンポーネントの両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7b96e-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger includes both server-side and client-side components.</span></span> <span data-ttu-id="7b96e-106">サーバー側のデバッガー コンポーネントは、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) 以降のデータベース エンジンの各インスタンスと共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-106">The server-side debugger components are installed with each instance of the Database Engine from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="7b96e-107">クライアント側のデバッガー コンポーネントは、以下の時点で含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-107">The client-side debugger components are included:</span></span>  
  
-   <span data-ttu-id="7b96e-108">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降からクライアント側のツールをインストールするとき。</span><span class="sxs-lookup"><span data-stu-id="7b96e-108">When you install the client-side tools from [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or later.</span></span>  
  
-   <span data-ttu-id="7b96e-109">microsoft visual studio 2010 以降をインストールするとき。</span><span class="sxs-lookup"><span data-stu-id="7b96e-109">When you install Microsoft Visual Studio 2010 or later.</span></span>  
  
-   <span data-ttu-id="7b96e-110">Web ダウンロードから [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] をインストールするとき。</span><span class="sxs-lookup"><span data-stu-id="7b96e-110">When you install [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] from the web download.</span></span>  
  
 <span data-ttu-id="7b96e-111">[!INCLUDE[tsql](../../includes/tsql-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] が [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] インスタンスと同じコンピューター上で実行されている場合は、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]デバッガーを実行するための構成要件はありません。</span><span class="sxs-lookup"><span data-stu-id="7b96e-111">There are no configuration requirements to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] is running on the same computer as the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="7b96e-112">ただし、 [!INCLUDE[tsql](../../includes/tsql-md.md)] のリモート インスタンスに接続するときに [!INCLUDE[ssDE](../../includes/ssde-md.md)]デバッガーを実行するには、Windows ファイアウォールのプログラムとポートの規則を両方のコンピューターで有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-112">However, to run the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger when connected to a remote instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], program and port rules in the Windows Firewall must be enabled on both computers.</span></span> <span data-ttu-id="7b96e-113">これらの規則は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップによって作成できます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-113">These rules may be created by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] setup.</span></span> <span data-ttu-id="7b96e-114">リモート デバッグ セッションを開こうとしたときにエラーが発生する場合は、次のファイアウォール規則がコンピューターに定義されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-114">If you get errors attempting to open a remote debugging session, ensure the following firewall rules are defined on your computer.</span></span>  
  
 <span data-ttu-id="7b96e-115">ファイアウォール規則を管理するには、 **セキュリティが強化された Windows ファイアウォール** アプリケーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-115">Use the **Windows Firewall with Advanced Security** application to manage the firewall rules.</span></span> <span data-ttu-id="7b96e-116">[!INCLUDE[win7](../../includes/win7-md.md)] と [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)]のどちらの場合でも、 **[コントロール パネル]** を開き、 **[Windows ファイアウォール]** を開いて **[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-116">In both [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)], open **Control Panel**, open **Windows Firewall**, and select **Advanced settings**.</span></span> <span data-ttu-id="7b96e-117">[!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] では、 **[サービス マネージャー]** を開き、左側のペインで **[構成]** を展開し、 **[セキュリティが強化された Windows ファイアウォール]** を展開することもできます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-117">In [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] you can also open **Service Manager**, expand **Configuration** in the left pane, and expand **Windows Firewall with Advanced Security**.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="7b96e-118">Windows ファイアウォール規則を有効にした場合、ファイアウォールでブロックするように指定されているセキュリティ上の脅威にコンピューターがさらされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-118">Enabling rules in the Windows Firewall may expose your computer to security threats that the firewall is designed to block.</span></span> <span data-ttu-id="7b96e-119">リモート デバッグ用の規則を有効にすると、このトピックで示されているポートとプログラムのブロックが解除されます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-119">Enabling rules for remote debugging unblocks the ports and programs listed in this topic.</span></span>  
  
## <a name="firewall-rules-on-the-server"></a><span data-ttu-id="7b96e-120">サーバー上のファイアウォール規則</span><span class="sxs-lookup"><span data-stu-id="7b96e-120">Firewall Rules on the Server</span></span>  
 <span data-ttu-id="7b96e-121">[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスが実行されているコンピューター上で、 **セキュリティが強化された Windows ファイアウォール** を使用して、次の情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-121">On the computer that is running the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)], use **Windows Firewall with Advanced Security** to specify the following information:</span></span>  
  
-   <span data-ttu-id="7b96e-122">sqlservr.exe の受信プログラム規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-122">Add an inbound program rule for sqlservr.exe.</span></span> <span data-ttu-id="7b96e-123">リモート デバッグ セッションをサポートする必要がある各インスタンス用の規則が必要です。</span><span class="sxs-lookup"><span data-stu-id="7b96e-123">You must have a rule for each instance that needs to support remote debugging sessions.</span></span>  
  
    1.  <span data-ttu-id="7b96e-124">**[セキュリティが強化された Windows ファイアウォール]** で、左側のペインの **[受信の規則]** をクリックし、[操作] ペインの **[新しい規則]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-124">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="7b96e-125">**[規則の種類]** ダイアログで、 **[プログラム]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-125">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="7b96e-126">**[プログラム]** ダイアログで、 **[このプログラムのパス:]** をクリックし、このインスタンスの sqlservr.exe の完全なパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-126">In the **Program** dialog, select **This program path:** and enter the full path to sqlservr.exe for this instance.</span></span> <span data-ttu-id="7b96e-127">既定では、sqlservr.exe は C:\Program の SQL Server\MSSQL12. にインストールされます。*Instancename*\MSSQL\Binn。 *instancename*は既定のインスタンスの場合は MSSQLSERVER、名前付きインスタンスの場合はインスタンス名です。</span><span class="sxs-lookup"><span data-stu-id="7b96e-127">By default, sqlservr.exe is installed in C:\Program Files\Microsoft SQL Server\MSSQL12.*InstanceName*\MSSQL\Binn, where *InstanceName* is MSSQLSERVER for the default instance, and the instance name for any named instance.</span></span>  
  
    4.  <span data-ttu-id="7b96e-128">**[操作]** ダイアログで、 **[接続を許可する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-128">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="7b96e-129">**[プロファイル]** ダイアログで、インスタンスとのデバッグ セッションを開くときのコンピューター接続環境を表すプロファイルをすべて選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-129">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="7b96e-130">**[名前]** ダイアログで、この規則の名前と説明を入力し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-130">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="7b96e-131">**[受信の規則]** の一覧で、作成した規則を右クリックし、[操作] ペインの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-131">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="7b96e-132">**[プロトコルおよびポート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-132">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="7b96e-133">**[プロトコルの種類:]** ボックスで **[TCP]** 、 **[ローカル ポート:]** ボックスで **[RPC 動的ポート]** を選択します。次に、 **[適用]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-133">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="7b96e-134">svchost.exe の受信プログラム規則を追加して、リモート デバッグ セッションからの DCOM 通信を有効にします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-134">Add an inbound program rule for svchost.exe to enable DCOM communications from remote debugger sessions.</span></span>  
  
    1.  <span data-ttu-id="7b96e-135">**[セキュリティが強化された Windows ファイアウォール]** で、左側のペインの **[受信の規則]** をクリックし、[操作] ペインの **[新しい規則]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-135">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="7b96e-136">**[規則の種類]** ダイアログで、 **[プログラム]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-136">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="7b96e-137">**[プログラム]** ダイアログで、 **[このプログラムのパス:]** をクリックし、svchost.exe の完全なパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-137">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="7b96e-138">既定では、svchost.exe は %systemroot%\System32\svchost.exe にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-138">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="7b96e-139">**[操作]** ダイアログで、 **[接続を許可する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-139">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="7b96e-140">**[プロファイル]** ダイアログで、インスタンスとのデバッグ セッションを開くときのコンピューター接続環境を表すプロファイルをすべて選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-140">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="7b96e-141">**[名前]** ダイアログで、この規則の名前と説明を入力し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-141">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="7b96e-142">**[受信の規則]** の一覧で、作成した規則を右クリックし、[操作] ペインの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-142">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="7b96e-143">**[プロトコルおよびポート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-143">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="7b96e-144">**[プロトコルの種類:]** ボックスで **[TCP]** 、 **[ローカル ポート:]** ボックスで **[RPC エンドポイント マッパー]** を選択します。次に、 **[適用]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-144">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="7b96e-145">ドメイン ポリシーにより IPSec 経由でネットワーク通信を行う必要がある場合は、UDP ポート 4500 と UDP ポート 500 を開く受信規則も追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-145">If the domain policy requires network communications to be done through IPsec, you must also add inbound rules opening UDP port 4500 and UDP port 500.</span></span>  
  
## <a name="firewall-rules-on-the-client"></a><span data-ttu-id="7b96e-146">クライアント上のファイアウォール規則</span><span class="sxs-lookup"><span data-stu-id="7b96e-146">Firewall Rules on the Client</span></span>  
 <span data-ttu-id="7b96e-147">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターを実行中のコンピューターでは、SQL Server セットアップまたは [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] セットアップで Windows ファイアウォールがリモート デバッグを許可するように構成されている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-147">On the computer that is running the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor, the SQL Server setup or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] setup may have configured the Windows Firewall to allow remote debugging.</span></span>  
  
 <span data-ttu-id="7b96e-148">リモート デバッグ セッションを開こうとしたときにエラーが発生する場合は、 **セキュリティが強化された Windows ファイアウォール** を使用してファイアウォール規則を構成することで、プログラムとポートの例外を手動で構成できます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-148">If you get errors attempting to open a remote debugging session, you can manually configure the program and port exceptions by using **Windows Firewall with Advanced Security** to configure firewall rules:</span></span>  
  
-   <span data-ttu-id="7b96e-149">svchost 用のプログラム エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-149">Add a program entry for svchost:</span></span>  
  
    1.  <span data-ttu-id="7b96e-150">**[セキュリティが強化された Windows ファイアウォール]** で、左側のペインの **[受信の規則]** をクリックし、[操作] ペインの **[新しい規則]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-150">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="7b96e-151">**[規則の種類]** ダイアログで、 **[プログラム]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-151">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="7b96e-152">**[プログラム]** ダイアログで、 **[このプログラムのパス:]** をクリックし、svchost.exe の完全なパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-152">In the **Program** dialog, select **This program path:** and enter the full path to svchost.exe.</span></span> <span data-ttu-id="7b96e-153">既定では、svchost.exe は %systemroot%\System32\svchost.exe にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-153">By default, svchost.exe is installed in %systemroot%\System32\svchost.exe.</span></span>  
  
    4.  <span data-ttu-id="7b96e-154">**[操作]** ダイアログで、 **[接続を許可する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-154">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="7b96e-155">**[プロファイル]** ダイアログで、インスタンスとのデバッグ セッションを開くときのコンピューター接続環境を表すプロファイルをすべて選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-155">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="7b96e-156">**[名前]** ダイアログで、この規則の名前と説明を入力し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-156">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="7b96e-157">**[受信の規則]** の一覧で、作成した規則を右クリックし、[操作] ペインの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-157">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="7b96e-158">**[プロトコルおよびポート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-158">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="7b96e-159">**[プロトコルの種類:]** ボックスで **[TCP]** 、 **[ローカル ポート:]** ボックスで **[RPC エンドポイント マッパー]** を選択します。次に、 **[適用]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-159">Select **TCP** in the **Protocol type:** box, select **RPC Endpoint Mapper** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
-   <span data-ttu-id="7b96e-160">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディターをホストするアプリケーション用のプログラム エントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-160">Add a program entry for the application hosting the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="7b96e-161">同じコンピューター上の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] からリモート デバッグ セッションを開く必要がある場合は、両方に対してプログラム規則を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-161">If you need to open remote debugging sessions from both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] on the same computer, you must add a program rule for both:</span></span>  
  
    1.  <span data-ttu-id="7b96e-162">**[セキュリティが強化された Windows ファイアウォール]** で、左側のペインの **[受信の規則]** をクリックし、[操作] ペインの **[新しい規則]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-162">In **Windows Firewall with Advanced Security**, in the left pane, right-click **Inbound Rules**, and then select **New Rule** in the action pane.</span></span>  
  
    2.  <span data-ttu-id="7b96e-163">**[規則の種類]** ダイアログで、 **[プログラム]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-163">In the **Rule Type** dialog, select **Program**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="7b96e-164">**[プログラム]** ダイアログで、 **[このプログラムのパス:]** をクリックし、次の 3 つの値のいずれかを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-164">In the **Program** dialog, select **This program path:** and enter one of these three values.</span></span>  
  
        -   <span data-ttu-id="7b96e-165">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]では、ssms.exe の完全パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-165">For [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], enter the full path to ssms.exe.</span></span> <span data-ttu-id="7b96e-166">既定では、ssms.exe は C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-166">By default, ssms.exe is installed in C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\Management Studio.</span></span>  
  
        -   <span data-ttu-id="7b96e-167">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] では、devenv.exe の完全パスを入力します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-167">For [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] enter the full path to devenv.exe:</span></span>  
  
            1.  <span data-ttu-id="7b96e-168">既定では、Visual Studio 2010 用の devenv.exe は、C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE に配置されます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-168">By default, the devenv.exe for Visual Studio 2010 is in C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\IDE.</span></span>  
  
            2.  <span data-ttu-id="7b96e-169">既定では、Visual Studio 2012 用の devenv.exe は、C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE に配置されます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-169">By default, the devenv.exe for Visual Studio 2012 is in C:\Program Files (x86)\Microsoft Visual Studio 11.0\Common7\IDE</span></span>  
  
            3.  <span data-ttu-id="7b96e-170">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を起動するために使用するショートカットで、ssms.exe のパスを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-170">You can find the path to ssms.exe from the shortcut you use to launch [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7b96e-171">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を起動するために使用するショートカットで、devenv.exe のパスを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-171">You can find the path to devenv.exe from the shortcut you use to launch [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)].</span></span> <span data-ttu-id="7b96e-172">ショートカットを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-172">Right click the shortcut and select **Properties**.</span></span> <span data-ttu-id="7b96e-173">実行可能ファイルとパスが **[ターゲット]** ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b96e-173">The executable and path are listed in the **Target** box.</span></span>  
  
    4.  <span data-ttu-id="7b96e-174">**[操作]** ダイアログで、 **[接続を許可する]** をクリックし、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-174">In the **Action** dialog, select **Allow the connection**, and click **Next**.</span></span>  
  
    5.  <span data-ttu-id="7b96e-175">**[プロファイル]** ダイアログで、インスタンスとのデバッグ セッションを開くときのコンピューター接続環境を表すプロファイルをすべて選択し、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-175">In the **Profile** dialog, select any profiles that describe the computer connection environment when you want to open a debugging session with the instance, and click **Next**.</span></span>  
  
    6.  <span data-ttu-id="7b96e-176">**[名前]** ダイアログで、この規則の名前と説明を入力し、 **[完了]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-176">In the **Name** dialog, type a name and description for this rule and click **Finish**.</span></span>  
  
    7.  <span data-ttu-id="7b96e-177">**[受信の規則]** の一覧で、作成した規則を右クリックし、[操作] ペインの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b96e-177">In the **Inbound Rules** list, right click the rule you created, and then select **Properties** in the action pane.</span></span>  
  
    8.  <span data-ttu-id="7b96e-178">**[プロトコルおよびポート]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-178">Select the **Protocols and Ports** tab.</span></span>  
  
    9. <span data-ttu-id="7b96e-179">**[プロトコルの種類:]** ボックスで **[TCP]** 、 **[ローカル ポート:]** ボックスで **[RPC 動的ポート]** を選択します。次に、 **[適用]** をクリックし、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b96e-179">Select **TCP** in the **Protocol type:** box, select **RPC Dynamic Ports** in the **Local port:** box, click **Apply**, and then click **OK**.</span></span>  
  
## <a name="requirements-for-starting-the-debugger"></a><span data-ttu-id="7b96e-180">デバッガーを起動するための要件</span><span class="sxs-lookup"><span data-stu-id="7b96e-180">Requirements for Starting the Debugger</span></span>  
 <span data-ttu-id="7b96e-181">[!INCLUDE[tsql](../../includes/tsql-md.md)] デバッガーを起動するには、次の要件をすべて満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-181">All attempts to start the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger must also meet the following requirements:</span></span>  
  
* [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7b96e-182">または [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] が、sysadmin 固定サーバー ロールのメンバーである Windows アカウントで実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-182">or [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] must be running under a Windows account that is a member of the sysadmin fixed server roll.</span></span>  
  
* <span data-ttu-id="7b96e-183">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウが、sysadmin 固定サーバー ロールのメンバーである Windows 認証または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証ログインを使用して接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-183">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected by using either a Windows Authentication or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Authentication login that is a member of the sysadmin fixed server role.</span></span>  
  
* <span data-ttu-id="7b96e-184">[!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウが、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] Service Pack 2 (SP2) 以降の [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] のインスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-184">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window must be connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 2 (SP2) or later.</span></span> <span data-ttu-id="7b96e-185">クエリ エディター ウィンドウがシングル ユーザー モードのインスタンスに接続されているときは、デバッガーを実行できません。</span><span class="sxs-lookup"><span data-stu-id="7b96e-185">You cannot run the debugger when the Query Editor window is connected to an instance that is in single-user mode.</span></span>

* <span data-ttu-id="7b96e-186">サーバーとクライアントが RPC 経由で通信をしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-186">The server needs to communicate back to the client via RPC.</span></span> <span data-ttu-id="7b96e-187">SQL Server サービスが実行されているアカウントは、クライアントに対する認証権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b96e-187">The account under which SQL Server service is running should have authenticate permissions to the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b96e-188">参照</span><span class="sxs-lookup"><span data-stu-id="7b96e-188">See Also</span></span>  
 <span data-ttu-id="7b96e-189">[Transact-sql デバッガー](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="7b96e-189">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="7b96e-190">[Transact-sql デバッガーの実行](run-the-transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="7b96e-190">[Run the Transact-SQL Debugger](run-the-transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="7b96e-191">[Transact-sql コードのステップ実行](step-through-transact-sql-code.md) </span><span class="sxs-lookup"><span data-stu-id="7b96e-191">[Step Through Transact-SQL Code](step-through-transact-sql-code.md) </span></span>  
 <span data-ttu-id="7b96e-192">[Transact-sql デバッガー情報](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="7b96e-192">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="7b96e-193">データベース エンジン クエリ エディター &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="7b96e-193">Database Engine Query Editor &#40;SQL Server Management Studio&#41;</span></span>](database-engine-query-editor-sql-server-management-studio.md)  
  
  
