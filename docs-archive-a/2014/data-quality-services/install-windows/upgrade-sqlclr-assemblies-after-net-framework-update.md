---
title: .NET Framework 更新後の SQLCLR アセンブリのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b1a008cc-7e6b-4655-a869-bd429f986400
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 45d60db413e11828f26bd03e1c8f350645838d12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641879"
---
# <a name="upgrade-sqlclr-assemblies-after-net-framework-update"></a><span data-ttu-id="e5698-102">.NET Framework 更新後の SQLCLR アセンブリのアップグレード</span><span class="sxs-lookup"><span data-stu-id="e5698-102">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>
  [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] <span data-ttu-id="e5698-103">(DQS) は、Microsoft .NET Framework 4 アセンブリを参照する SQL 共通言語ランタイム (SQLCR) ルーチンのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="e5698-103">(DQS) is a collection of SQL Common Language Runtime (SQLCR) routines that reference Microsoft .NET Framework 4 assemblies.</span></span> <span data-ttu-id="e5698-104">コンピューターの .NET Framework を更新し、それが参照先の .NET Framework アセンブリに影響した場合、グローバル アセンブリ キャッシュ (GAC) 内のアセンブリのモジュール バージョン ID (MVID) が変更されます。</span><span class="sxs-lookup"><span data-stu-id="e5698-104">When you install any .NET Framework updates on your computer that affect any such referenced .NET Framework assembly, it leads to a change in the Module Version ID (MVID) of the assembly in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="e5698-105">これが起こると、GAC 内の参照先アセンブリと [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]内のアセンブリとの間で MVID の不一致が発生します。</span><span class="sxs-lookup"><span data-stu-id="e5698-105">This causes a mismatch between the MVIDs of the referenced assembly in GAC and the assembly in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="e5698-106">.NET Framework の更新で [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンピューターの再起動が必要な場合は、影響を受ける SQLCLR アセンブリが自動的にアップグレードされて、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンピューターの再起動時に発生する MVID の不一致の問題が修正されます。</span><span class="sxs-lookup"><span data-stu-id="e5698-106">If the .NET Framework update requires you to restart the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, the affected SQLCLR assemblies are upgraded automatically to fix the MVID mismatch issue on restarting the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span> <span data-ttu-id="e5698-107">ただし、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンピューターを再起動する必要のない .NET Framework の更新の場合は、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] を使用して [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]に接続しようとすると、アセンブリの MVID の不一致によりエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="e5698-107">However, for .NET Framework updates that do not require you to restart your [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer, an error occurs due to the mismatch in the MVIDs of the assemblies when you try to connect to a [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] using a [!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]:</span></span>  
  
```  
A new version of .NET was installed on this machine. In order to continue to work with DQS please run dqsinstaller.exe -upgradedlls.  
```  
  
 <span data-ttu-id="e5698-108">この問題を解決するには、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 内の、影響を受ける SQLCLR アセンブリをアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5698-108">To fix this issue, the affected SQLCLR assemblies in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be upgraded.</span></span> <span data-ttu-id="e5698-109">これを行うには、 **upgradedlls** コマンド ライン パラメーターを使用して DQSInstaller.exe ファイルを実行することにより、DQS データベースの再作成をスキップし、影響を受けるアセンブリのアップグレードのみを行います。</span><span class="sxs-lookup"><span data-stu-id="e5698-109">You can do so by running the DQSInstaller.exe file with the **upgradedlls** command line parameter to skip recreating the DQS databases, and just upgrade the affected assemblies.</span></span> <span data-ttu-id="e5698-110">これにより、ナレッジ ベース、データ品質プロジェクト、および DQS 内のその他すべてのデータが維持されます。</span><span class="sxs-lookup"><span data-stu-id="e5698-110">This ensures that your knowledge bases, data quality projects, and any other data in DQS are preserved.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e5698-111">前提条件</span><span class="sxs-lookup"><span data-stu-id="e5698-111">Prerequisites</span></span>  
  
-   <span data-ttu-id="e5698-112">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンピューターの Administrators グループのメンバーとしてログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5698-112">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="e5698-113">Windows ユーザー アカウントが、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] がインストールされている SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="e5698-113">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-sqlclr-assemblies"></a><span data-ttu-id="e5698-114">SQLCLR アセンブリをアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="e5698-114">To upgrade SQLCLR Assemblies</span></span>  
  
1.  <span data-ttu-id="e5698-115">コマンド プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="e5698-115">Start Command Prompt.</span></span>  
  
2.  <span data-ttu-id="e5698-116">コマンド プロンプトで、DQSInstaller.exe が格納されている場所にディレクトリを変更します。</span><span class="sxs-lookup"><span data-stu-id="e5698-116">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="e5698-117">SQL Server の既定のインスタンスをインストールした場合、DQSInstaller.exe ファイルは C:\Program Server\MSSQL12. にあります。MSSQLSERVER\MSSQL\Binn:</span><span class="sxs-lookup"><span data-stu-id="e5698-117">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
3.  <span data-ttu-id="e5698-118">コマンド プロンプトに次のコマンドを入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e5698-118">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgradedlls  
    ```  
  
4.  <span data-ttu-id="e5698-119">残りの手順は、「 [Data Quality Server のインストールを完了するための DQSInstaller.exe の実行](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) 」の「 [[スタート] 画面、[スタート] メニュー、または Windows エクスプローラーから DQSInstaller.exe を実行する](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)」の手順 2. ～ 6. と同じです。</span><span class="sxs-lookup"><span data-stu-id="e5698-119">Rest of the steps are same as steps 2-6 in the [Run DQSInstaller.exe from Start Screen, Start Menu or Windows Explorer](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md#WindowsExplorer) section in [Run DQSInstaller.exe to Complete Data Quality Server Installation](run-dqsinstaller-exe-to-complete-data-quality-server-installation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5698-120">参照</span><span class="sxs-lookup"><span data-stu-id="e5698-120">See Also</span></span>  
 <span data-ttu-id="e5698-121">[Data Quality Services のインストール](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="e5698-121">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="e5698-122">SQL Server 更新プログラムのインストール後の DQS データベース スキーマのアップグレード</span><span class="sxs-lookup"><span data-stu-id="e5698-122">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>](upgrade-dqs-databases-schema-after-installing-sql-server-update.md)  
  
  
