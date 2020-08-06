---
title: SQL Server 更新プログラムのインストール後の DQS データベース スキーマのアップグレード | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: c8f3fbae-02c4-464d-a35c-7108f48c58cb
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 80a1714ea250cf7cf5d34bc9d208a42a64284308
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641881"
---
# <a name="upgrade-dqs-databases-schema-after-installing-sql-server-update"></a><span data-ttu-id="55bb1-102">SQL Server 更新プログラムのインストール後の DQS データベース スキーマのアップグレード</span><span class="sxs-lookup"><span data-stu-id="55bb1-102">Upgrade DQS Databases Schema After Installing SQL Server Update</span></span>
  <span data-ttu-id="55bb1-103">あらかじめ構成された DQS インスタンスに SQL Server の更新プログラム (パッチ、修正プログラム、または累積的な更新プログラム) をインストールした後、 **upgrade** コマンド ライン パラメーターを指定して DQSInstaller.exe ファイルを実行し、DQS データベース スキーマをアップグレードする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="55bb1-103">After you have installed a SQL Server update (patch, hotfix, or cumulative update) on a previously configured DQS instance, you might have to upgrade the DQS databases schema by running the DQSInstaller.exe file with the **upgrade** command line parameter.</span></span> <span data-ttu-id="55bb1-104">アップグレードしなかった場合、Data Quality Client を使用して Data Quality Server に接続しようとすると、次のエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="55bb1-104">Otherwise, you might receive the following error while trying to connect to Data Quality Server using your Data Quality Client:</span></span>  
  
```  
An error occurred in the Microsoft .NET Framework while trying to load assembly id 65581.  
```  
  
 <span data-ttu-id="55bb1-105">DQS データベース スキーマのアップグレードは、DQS データベース内の既存のデータ (ナレッジ ベース、データ品質プロジェクト、DQS_STAGING_DATA データベース内にエクスポートされた結果) には影響しません。</span><span class="sxs-lookup"><span data-stu-id="55bb1-105">Upgrading DQS databases schema does not impact your existing data in the DQS databases (knowledge bases, data quality projects, and exported results in the DQS_STAGING_DATA database).</span></span> <span data-ttu-id="55bb1-106">ただし、スキーマのアップグレード中に誤ってデータが削除されることを防ぐため、DQS データベース スキーマをアップグレードする前に DQS データベースをバックアップしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="55bb1-106">However, you must back up your DQS databases before upgrading DQS databases schema to prevent any accidental data loss during the schema upgrade.</span></span> <span data-ttu-id="55bb1-107">DQS データベースのバックアップの詳細については、「 [DQS データベースのバックアップと復元](../backing-up-and-restoring-dqs-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55bb1-107">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55bb1-108">SQL Server の更新プログラムのほとんどで、DQS データベース スキーマのアップグレードが必要になります。</span><span class="sxs-lookup"><span data-stu-id="55bb1-108">Most of the SQL Server updates will require an upgrade to the DQS databases schema.</span></span> <span data-ttu-id="55bb1-109">DQS データベース スキーマのアップグレードが必要になる SQL Server 更新プログラムの詳細については、「 [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)」(DQS のアップグレード: Data Quality Services への累積的な更新プログラムまたは修正プログラムのインストール) の手順 1.A にある表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55bb1-109">For information about the SQL Server updates that will require an upgrade to the DQS databases schema, see the chart in step 1.A in [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="55bb1-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="55bb1-110">Prerequisites</span></span>  
  
-   <span data-ttu-id="55bb1-111">[!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] コンピューターの Administrators グループのメンバーとしてログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="55bb1-111">You must be logged on as a member of the Administrators group on the [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] computer.</span></span>  
  
-   <span data-ttu-id="55bb1-112">Windows ユーザー アカウントが、 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] がインストールされている SQL Server インスタンスの sysadmin 固定サーバー ロールのメンバーであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="55bb1-112">Your Windows user account must be a member of the sysadmin fixed server role in the SQL Server instance where [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] is installed.</span></span>  
  
### <a name="to-upgrade-dqs-databases-schema"></a><span data-ttu-id="55bb1-113">DQS データベース スキーマをアップグレードするには</span><span class="sxs-lookup"><span data-stu-id="55bb1-113">To upgrade DQS databases schema</span></span>  
  
1.  <span data-ttu-id="55bb1-114">(推奨) スキーマのアップグレードを実行する前に、DQS データベースをバックアップします。</span><span class="sxs-lookup"><span data-stu-id="55bb1-114">(Recommended) Back up your DQS databases before you proceed with the schema upgrade.</span></span> <span data-ttu-id="55bb1-115">DQS データベースのバックアップの詳細については、「 [DQS データベースのバックアップと復元](../backing-up-and-restoring-dqs-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55bb1-115">For information about backing up DQS databases, see [Backing Up and Restoring DQS Databases](../backing-up-and-restoring-dqs-databases.md).</span></span>  
  
2.  <span data-ttu-id="55bb1-116">コマンド プロンプトを起動します。</span><span class="sxs-lookup"><span data-stu-id="55bb1-116">Start Command Prompt.</span></span>  
  
3.  <span data-ttu-id="55bb1-117">コマンド プロンプトで、DQSInstaller.exe が格納されている場所にディレクトリを変更します。</span><span class="sxs-lookup"><span data-stu-id="55bb1-117">At the command prompt, change your directory to the location where DQSInstaller.exe is available.</span></span> <span data-ttu-id="55bb1-118">SQL Server の既定のインスタンスをインストールした場合、DQSInstaller.exe ファイルは C:\Program Server\MSSQL12. にあります。MSSQLSERVER\MSSQL\Binn:</span><span class="sxs-lookup"><span data-stu-id="55bb1-118">If you installed the default instance of SQL Server, the DQSInstaller.exe file will be available at C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn:</span></span>  
  
    ```  
    cd C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn  
    ```  
  
4.  <span data-ttu-id="55bb1-119">コマンド プロンプトに次のコマンドを入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="55bb1-119">At the command prompt, type the following command, and press ENTER:</span></span>  
  
    ```  
    dqsinstaller.exe -upgrade  
    ```  
  
5.  <span data-ttu-id="55bb1-120">処理を続ける前に DQS データベースをバックアップするように求められます。</span><span class="sxs-lookup"><span data-stu-id="55bb1-120">The installer prompts you for backing up the DQS databases before proceeding.</span></span> <span data-ttu-id="55bb1-121">既に DQS データベースをバックアップしている場合は「`Y`」または「`Yes`」と入力して Enter キーを押し、アップグレードを続行します。</span><span class="sxs-lookup"><span data-stu-id="55bb1-121">If you have already backed up your DQS databases, type `Y` or `Yes` and press ENTER to continue with the upgrade.</span></span>  
  
6.  <span data-ttu-id="55bb1-122">DQS データベース スキーマのアップグレードが正常に完了すると、完了のメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="55bb1-122">A completion message is displayed after successful upgrade of the DQS databases schema.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="55bb1-123">次の手順</span><span class="sxs-lookup"><span data-stu-id="55bb1-123">Next Steps</span></span>  
 <span data-ttu-id="55bb1-124">Data Quality Client アプリケーションから、アップグレードされた Data Quality Server にログオンします。</span><span class="sxs-lookup"><span data-stu-id="55bb1-124">Log on to the upgraded Data Quality Server from a Data Quality Client application.</span></span>  
  
 <span data-ttu-id="55bb1-125">SQL Server の更新プログラムをインストールしてからの DQS データベース スキーマのアップグレードの詳細、および関連するトラブルシューティング手順については、「 [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565)」(DQS のアップグレード: Data Quality Services への累積的な更新プログラムまたは修正プログラムのインストール) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55bb1-125">For more information about upgrading DQS databases schema after installing SQL Server updates and associated troubleshooting steps, see [Upgrade DQS: Installing Cumulative Updates or Hotfix Patches on Data Quality Services](https://go.microsoft.com/fwlink/?LinkID=251565).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55bb1-126">参照</span><span class="sxs-lookup"><span data-stu-id="55bb1-126">See Also</span></span>  
 <span data-ttu-id="55bb1-127">[Data Quality Services のインストール](install-data-quality-services.md) </span><span class="sxs-lookup"><span data-stu-id="55bb1-127">[Install Data Quality Services](install-data-quality-services.md) </span></span>  
 [<span data-ttu-id="55bb1-128">.NET Framework 更新後の SQLCLR アセンブリのアップグレード</span><span class="sxs-lookup"><span data-stu-id="55bb1-128">Upgrade SQLCLR Assemblies After .NET Framework Update</span></span>](upgrade-sqlclr-assemblies-after-net-framework-update.md)  
  
  
