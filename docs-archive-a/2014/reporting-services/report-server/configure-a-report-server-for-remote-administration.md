---
title: リモート管理用のレポート サーバーの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Reporting Services Configuration tool
- WMI provider [Reporting Services], remote configuration
- configuration management [WMI]
- report servers [Reporting Services], configuring
- remote server administration [Reporting Services]
ms.assetid: 8c7f145f-3ac2-4203-8cd6-2a4694395d09
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2c34db5299fc1b82a7896a41519e55466c3b3b79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642566"
---
# <a name="configure-a-report-server-for-remote-administration"></a><span data-ttu-id="f1bec-102">リモート管理用のレポート サーバーの構成</span><span class="sxs-lookup"><span data-stu-id="f1bec-102">Configure a Report Server for Remote Administration</span></span>
  <span data-ttu-id="f1bec-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]では、レポート サーバー インスタンスをローカルでもリモートでも構成できます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you can configure report server instances locally or remotely.</span></span> <span data-ttu-id="f1bec-104">リモートのレポート サーバー インスタンスを構成するには、Reporting Services 構成ツールを使用するか、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] WMI (Windows Management Instrumentation) プロバイダーを利用するカスタム コードを作成します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-104">To configure a remote report server instance, you can use the Reporting Services Configuration tool or write custom code that uses the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Windows Management Instrumentation (WMI) provider.</span></span> <span data-ttu-id="f1bec-105">Reporting Services 構成ツールには WMI プロバイダーのグラフィカル インターフェイスが用意されているので、コードを記述しなくてもレポート サーバーの構成を行えます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-105">The Reporting Services Configuration tool provides a graphical interface to the WMI provider so that you can configure a report server without having to write code.</span></span> <span data-ttu-id="f1bec-106">このツールを起動する際に、接続先のリモート サーバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-106">When you start the tool, you can specify a remote server to connect to.</span></span>  
  
 <span data-ttu-id="f1bec-107">ツールを使用してリモートのレポート サーバーを構成するには、このトピックの説明に従って Windows ファイアウォールでポートを有効にし、リモート接続とリモート WMI 要求も有効にしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-107">Before you can use the tool to configure a remote report server, you must follow the instructions in this topic to enable ports in Windows Firewall, enable remote connections, and enable remote WMI requests.</span></span>  
  
 <span data-ttu-id="f1bec-108">適切な構成を行うと、次のエラーを回避できます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-108">Proper configuration helps you avoid the following error:</span></span>  
  
 `The machine could not be found.`  
  
 `"The RPC server is unavailable. (Exception from HRESULT: 0x800706BA)".`  
  
## <a name="prerequisites"></a><span data-ttu-id="f1bec-109">前提条件</span><span class="sxs-lookup"><span data-stu-id="f1bec-109">Prerequisites</span></span>  
 <span data-ttu-id="f1bec-110">ファイアウォールの設定を変更するには、ローカルの Administrators グループのメンバーとして、ローカルでログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-110">To modify firewall settings, you must be logged on locally and you must be a member of the local Administrators group.</span></span> <span data-ttu-id="f1bec-111">リモート接続を経由してリモート コンピューターの Windows のファイアウォール設定を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="f1bec-111">You cannot modify the Windows firewall settings of a remote computer over a remote connection.</span></span>  
  
 <span data-ttu-id="f1bec-112">管理者以外のユーザーがリモート管理を実行できるようにするには、DCOM (Distributed Component Object Model) の "リモートからのアクティブ化" アクセス許可をアカウントに与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-112">If you want to enable remote administration for a non-administrator user, you must grant the account Distributed Component Object Model (DCOM) Remote Activation permissions.</span></span> <span data-ttu-id="f1bec-113">管理者以外のユーザーがアクセスできるようにサーバーを構成する手順は、このトピックで説明します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-113">Instructions for configuring the server for non-administrator access are provided in this topic.</span></span>  
  
 <span data-ttu-id="f1bec-114">組織によっては、特定のオペレーティング システムまたはユーザーに対して、リモート サーバー管理を禁じるグループ ポリシーが定められている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-114">Some organizations have group policies that prevent remote server administration for certain operating systems or users.</span></span> <span data-ttu-id="f1bec-115">ファイアウォールの設定を変更する前に、リモート管理に対する制限があるかどうかをネットワーク管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="f1bec-115">Before you begin modifying firewall settings, check with your network administrator to verify whether there are restrictions on remote administration.</span></span>  
  
 <span data-ttu-id="f1bec-116">詳細については、MSDN のプラットフォーム SDK ドキュメントの「 [Windows ファイアウォールを使用した接続](https://go.microsoft.com/fwlink/?LinkId=63615) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bec-116">For more information, see [Connecting Through Windows Firewall](https://go.microsoft.com/fwlink/?LinkId=63615) in the Platform SDK documentation on MSDN.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="f1bec-117">処理手順</span><span class="sxs-lookup"><span data-stu-id="f1bec-117">Tasks</span></span>  
 <span data-ttu-id="f1bec-118">リモートのレポート サーバー構成を有効にするタスクは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f1bec-118">Tasks that enable remote report server configuration include the following:</span></span>  
  
-   <span data-ttu-id="f1bec-119">Windows ファイアウォールでポートを有効にし、レポート サーバーおよび SQL Server データベース エンジン インスタンスによって使用されるポートで要求が許可されるようにします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-119">Enable ports in Windows Firewall to allow requests on ports used by the report server and by the SQL Server Database Engine instance.</span></span>  
  
-   <span data-ttu-id="f1bec-120">レポート サーバー データベースをホストするデータベース エンジン インスタンスへのリモート接続を有効にします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-120">Enable remote connections to the instance of the Database Engine instance that hosts the report server database.</span></span> <span data-ttu-id="f1bec-121">リモート接続は、レポート サーバー データベース接続の構成と暗号化キーの管理のために必要です。</span><span class="sxs-lookup"><span data-stu-id="f1bec-121">A remote connection is necessary for configuring the report server database connection and managing the encryption keys.</span></span>  
  
-   <span data-ttu-id="f1bec-122">リモート WMI 要求が [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ファイアウォールを通過できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-122">Enable remote WMI requests to pass through the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows firewall.</span></span>  
  
-   <span data-ttu-id="f1bec-123">管理者以外のユーザーが管理を実行できるようにリモートのレポート サーバーを構成するには、DCOM 権限の設定で、標準 Windows ユーザー アカウントに対してリモート WMI アクセスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-123">If you are configuring a remote report server for administration by a non-administrative user, you must set DCOM permissions to enable remote WMI access to a standard Windows user account.</span></span> <span data-ttu-id="f1bec-124">WMI ではリモート呼び出しのトランスポートとして DCOM を使用するため、ローカル管理者としてログオンしていないユーザーがサーバーを構成できるようにするには、DCOM 権限を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-124">Because WMI uses DCOM as transport for remote calls, you must set the DCOM permissions so that users who are not logged on as the local administrator can configure the server.</span></span>  
  
-   <span data-ttu-id="f1bec-125">管理者以外のユーザーが管理を実行できるようにリモートのレポート サーバーを構成するには、レポート サーバーの WMI 名前空間に対する WMI 権限も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-125">If you are configuring a remote report server for administration by a non-administrative user, you must also set WMI permissions on the report server WMI namespace.</span></span> <span data-ttu-id="f1bec-126">既定では、ローカルの Administrator グループの全メンバーがレポート サーバーの WMI 名前空間にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-126">By default, all members of the local Administrator group have access to the report server WMI namespace.</span></span> <span data-ttu-id="f1bec-127">管理者以外のユーザーにアクセスを許可するには、アクセス許可を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1bec-127">If you want to grant access to non-administrators, you must set permissions.</span></span>  
  
 <span data-ttu-id="f1bec-128">このトピックでは、これらのタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-128">Instructions on how to perform these tasks are provided in this topic.</span></span>  
  
### <a name="to-open-ports-in-windows-firewall"></a><span data-ttu-id="f1bec-129">Windows ファイアウォールでポートを開くには</span><span class="sxs-lookup"><span data-stu-id="f1bec-129">To open ports in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="f1bec-130">[データベースエンジンアクセスできるように Windows ファイアウォールを構成](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-130">[Configure a Windows Firewall for Database Engine Access](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md).</span></span>  
  
2.  <span data-ttu-id="f1bec-131">[レポートサーバーアクセス用のファイアウォールを構成](configure-a-firewall-for-report-server-access.md)します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-131">[Configure a Firewall for Report Server Access](configure-a-firewall-for-report-server-access.md).</span></span>  
  
### <a name="to-configure-remote-connections-to-the-report-server-database"></a><span data-ttu-id="f1bec-132">レポート サーバー データベースへのリモート接続を構成するには</span><span class="sxs-lookup"><span data-stu-id="f1bec-132">To configure remote connections to the report server database</span></span>  
  
1.  <span data-ttu-id="f1bec-133">**[スタート]** ボタンをクリックし、 **[プログラム]**、[ [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-133">Click **Start**, point to **Programs**, point to [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], point to **Configuration Tools**, and click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="f1bec-134">左側のペインで、 **[SQL Server ネットワークの構成]** を展開し、 **のインスタンスの** [プロトコル] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-134">In the left pane, expand **SQL Server Network Configuration**, and then click **Protocols** for the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="f1bec-135">詳細ペインで TCP/IP プロトコルおよび名前付きパイプ プロトコルを有効にし、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-135">In the details pane, enable the TCP/IP and Named Pipes protocols, and then restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  
### <a name="to-enable-remote-administration-in-windows-firewall"></a><span data-ttu-id="f1bec-136">Windows ファイアウォールでリモート管理を有効にするには</span><span class="sxs-lookup"><span data-stu-id="f1bec-136">To enable remote administration in Windows Firewall</span></span>  
  
1.  <span data-ttu-id="f1bec-137">リモート管理を有効にするコンピューターに、ローカル管理者としてログオンします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-137">Log on as a local administrator to the computer for which you want to enable remote administration.</span></span>  
  
2.  <span data-ttu-id="f1bec-138">レポートサーバーが Windows Vista で実行されている場合は、[**コマンドプロンプト**] を右クリックし、[**管理者として実行**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-138">If the report server is running on Windows Vista, right-click **Command Prompt** and select **Run as administrator**.</span></span> <span data-ttu-id="f1bec-139">その他のオペレーティング システムの場合は、コマンド プロンプト ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-139">For other operating systems, open a command prompt window.</span></span>  
  
3.  <span data-ttu-id="f1bec-140">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-140">Run the following command:</span></span>  
  
    ```  
    netsh.exe firewall set service type=REMOTEADMIN mode=ENABLE scope=ALL  
    ```  
  
     <span data-ttu-id="f1bec-141">スコープには他のオプションも指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-141">You can specify different options for Scope.</span></span> <span data-ttu-id="f1bec-142">詳細については、Windows ファイアウォールのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1bec-142">For more information, see the Windows Firewall product documentation.</span></span>  
  
4.  <span data-ttu-id="f1bec-143">リモート管理が有効になったかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-143">Verify that remote administration is enabled.</span></span> <span data-ttu-id="f1bec-144">次のコマンドを実行して、状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-144">You can run the following command to show the status:</span></span>  
  
    ```  
    netsh.exe firewall show state  
    ```  
  
5.  <span data-ttu-id="f1bec-145">コンピューターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-145">Reboot the computer.</span></span>  
  
### <a name="to-set-dcom-permissions-to-enable-remote-wmi-access-for-non-administrators"></a><span data-ttu-id="f1bec-146">DCOM 権限を設定して管理者以外のユーザーによるリモート WMI アクセスを有効にするには</span><span class="sxs-lookup"><span data-stu-id="f1bec-146">To set DCOM permissions to enable remote WMI access for non-administrators</span></span>  
  
1.  <span data-ttu-id="f1bec-147">[スタート] メニューで、 **[管理ツール]** をポイントし、 **[コンポーネント サービス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-147">On the Start menu, point to **Administrative Tools**, click **Component Services**.</span></span>  
  
     <span data-ttu-id="f1bec-148">Windows Vista の場合は、[スタート] メニューの [**すべてのプログラム**] をクリックし、[**実行**] をクリックして、「」と入力し `mmc comexp.msc` ます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-148">For Windows Vista, on the Start menu, click **All Programs**, click **Run**, and then enter `mmc comexp.msc`.</span></span>  
  
2.  <span data-ttu-id="f1bec-149">[コンポーネント サービス] フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-149">Open the Component Services folder.</span></span>  
  
3.  <span data-ttu-id="f1bec-150">[コンピューター] フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-150">Open the Computers folder.</span></span>  
  
4.  <span data-ttu-id="f1bec-151">[マイ コンピューター] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-151">Select My Computer.</span></span>  
  
5.  <span data-ttu-id="f1bec-152">**[操作]** メニューの **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-152">On the **Action** menu, and select **Properties**.</span></span>  
  
6.  <span data-ttu-id="f1bec-153">**[COM セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-153">Click **COM Security**.</span></span>  
  
7.  <span data-ttu-id="f1bec-154">**[起動とアクティブ化のアクセス許可]** で、 **[制限の編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-154">In **Launch and Activation Permissions**, click **Edit Limits**.</span></span>  
  
8.  <span data-ttu-id="f1bec-155">**[起動許可]** に自分の名前が表示されない場合は、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-155">If you do not see your name in **Launch Permission**, click **Add**.</span></span>  
  
9. <span data-ttu-id="f1bec-156">自分のアカウントの名前を入力して、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-156">Type the name of your user account, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="f1bec-157">[許可] の **[許可] 列で**、[リモートからの**起動**] と [リモートから**の \<User or Group> \*\*\*\*アクティブ化**] を選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-157">In **Permissions for \<User or Group>**, in the **Allow** column, select **Remote Launch** and **Remote Activation**, and then click **OK**.</span></span>  
  
### <a name="to-set-permissions-on-the-report-server-wmi-namespace-for-non-administrators"></a><span data-ttu-id="f1bec-158">管理者以外のユーザーにレポート サーバーの WMI 名前空間に対する権限を設定するには</span><span class="sxs-lookup"><span data-stu-id="f1bec-158">To set permissions on the report server WMI namespace for non-administrators</span></span>  
  
1.  <span data-ttu-id="f1bec-159">[スタート] メニューで、 **[管理ツール]** をポイントし、 **[コンピューターの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-159">On the Start menu, point to **Administrative Tools**, click **Computer Management**.</span></span>  
  
2.  <span data-ttu-id="f1bec-160">[サービスとアプリケーション] フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-160">Open the Services and Applications folder.</span></span>  
  
3.  <span data-ttu-id="f1bec-161">**[WMI コントロール]** を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-161">Right-click **WMI Control**, and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="f1bec-162">**[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-162">Click **Security**.</span></span>  
  
5.  <span data-ttu-id="f1bec-163">Root フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-163">Open the Root folder.</span></span>  
  
6.  <span data-ttu-id="f1bec-164">Microsoft フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-164">Open the Microsoft folder.</span></span>  
  
7.  <span data-ttu-id="f1bec-165">SQLServer フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-165">Open the SQLServer folder.</span></span>  
  
8.  <span data-ttu-id="f1bec-166">ReportServer フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-166">Open the ReportServer folder.</span></span>  
  
9. <span data-ttu-id="f1bec-167">インスタンス フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-167">Open instance folder.</span></span> <span data-ttu-id="f1bec-168">既定のインスタンスをインストールした場合、フォルダーは MSSQLSERVER です。</span><span class="sxs-lookup"><span data-stu-id="f1bec-168">If you installed the default instance, the folder is MSSQLSERVER.</span></span>  
  
10. <span data-ttu-id="f1bec-169">v10 フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f1bec-169">Open the v10 folder.</span></span>  
  
11. <span data-ttu-id="f1bec-170">Admin フォルダーを選択し、 **[セキュリティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-170">Select the Admin folder, and then click **Security**.</span></span>  
  
12. <span data-ttu-id="f1bec-171">**[追加]** をクリックして、サーバーを管理するために使用するユーザー アカウントを入力します。</span><span class="sxs-lookup"><span data-stu-id="f1bec-171">Click **Add**, and then type the user account you will use to manage the server.</span></span>  
  
13. <span data-ttu-id="f1bec-172">**[許可]** 列の **[アカウントの有効化]**、 **[リモートの有効化]**、 **[セキュリティの読み取り]** をオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f1bec-172">In the **Allow** column, select **Enable Account**, **Remote Enable**, and **Read Security**, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bec-173">参照</span><span class="sxs-lookup"><span data-stu-id="f1bec-173">See Also</span></span>  
 [<span data-ttu-id="f1bec-174">Reporting Services 構成マネージャー &#40;ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="f1bec-174">Reporting Services Configuration Manager &#40;Native Mode&#41;</span></span>](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)  
  
  
