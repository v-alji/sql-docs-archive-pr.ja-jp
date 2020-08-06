---
title: リモートパーティションの作成と管理 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], remote
- remote partitions [Analysis Services]
ms.assetid: 4322b5cb-af07-4e79-8ecb-59e1121a9eb8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bd44775a579cc8f770f088594653bb65000407f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631274"
---
# <a name="create-and-manage-a-remote-partition-analysis-services"></a><span data-ttu-id="a4704-102">リモート パーティションの作成と管理 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="a4704-102">Create and Manage a Remote Partition (Analysis Services)</span></span>
  <span data-ttu-id="a4704-103">メジャー グループをパーティション分割する場合は、パーティションのストレージとして [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンスでセカンダリ データベースを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a4704-103">When partitioning a measure group, you can configure a secondary database on a remote [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance as partition storage.</span></span>  
  
 <span data-ttu-id="a4704-104">キューブ (master データベースと呼ばれます) のリモート パーティションは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のリモート インスタンス上の専用の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース (セカンダリ データベースと呼ばれます) に格納されています。</span><span class="sxs-lookup"><span data-stu-id="a4704-104">Remote partitions for a cube (called the master database) are stored in a dedicated [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] (called the secondary database).</span></span>  
  
 <span data-ttu-id="a4704-105">専用のセカンダリ データベースは、1 つの master データベースのみのリモート パーティションを格納できます。これに対し、master データベースは、すべてのセカンダリ データベースが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の同一のリモート インスタンスに存在する場合に限り、複数のセカンダリ データベースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4704-105">A dedicated secondary database can store remote partitions for one and only one master database, but the master database can use multiple secondary databases, as long as all the secondary databases are on the same remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a4704-106">リモート パーティション専用のデータベース内のディメンションは、リンク ディメンションとして作成されます。</span><span class="sxs-lookup"><span data-stu-id="a4704-106">Dimensions in a database dedicated to remote partitions are created as linked dimensions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a4704-107">前提条件</span><span class="sxs-lookup"><span data-stu-id="a4704-107">Prerequisites</span></span>  
 <span data-ttu-id="a4704-108">リモート パーティションを作成するには、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-108">Before you create a remote partition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="a4704-109">パーティションを格納するために、もう 1 つの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスと専用データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4704-109">You must have a second [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance and dedicated database to store the partitions.</span></span> <span data-ttu-id="a4704-110">セカンダリ データベースには、master データベースのリモート パーティションのストレージを提供するという専用の目的があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-110">The secondary database is single-purpose; it provides storage of remote partitions for a master database.</span></span>  
  
-   <span data-ttu-id="a4704-111">両方のサーバー インスタンスが同じバージョンであることが必要です。</span><span class="sxs-lookup"><span data-stu-id="a4704-111">Both server instances must be the same version.</span></span> <span data-ttu-id="a4704-112">両方のデータベースの機能レベルは同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-112">Both databases should be the same functional level.</span></span>  
  
-   <span data-ttu-id="a4704-113">両方のインスタンスが TCP 接続用に構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-113">Both instances must be configured for TCP connections.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a4704-114">は、HTTP プロトコルの使用によるリモート パーティションの作成をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="a4704-114">does not support creation of remote partitions by using the HTTP protocol.</span></span>  
  
-   <span data-ttu-id="a4704-115">両方のコンピューターのファイアウォール設定は、外部接続を許可するように設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-115">Firewall settings on both computers must be set to accept outside connections.</span></span> <span data-ttu-id="a4704-116">ファイアウォールの設定の詳細については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4704-116">For information about setting the firewall, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
-   <span data-ttu-id="a4704-117">master データベースを実行するインスタンスのサービス アカウントには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のリモート インスタンスに対する管理アクセス権が必要です。</span><span class="sxs-lookup"><span data-stu-id="a4704-117">The service account for the instance running the master database must have administrative access to the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a4704-118">サービス アカウントが変更された場合は、サーバーとデータベース両方に対する権限を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-118">If the service account changes, you must update permissions on both the server and database.</span></span>  
  
-   <span data-ttu-id="a4704-119">両方のコンピューターで [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-119">You must be an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] administrator on both computers.</span></span>  
  
-   <span data-ttu-id="a4704-120">ディザスター リカバリー計画がリモート パーティションのバックアップと復元に対応していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-120">You must ensure your disaster recovery plan accommodates backup and restore of the remote partitions.</span></span> <span data-ttu-id="a4704-121">リモート パーティションを使用すると、バックアップ操作と復元操作が複雑になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-121">Using remote partitions can complicate backup and restore operations.</span></span> <span data-ttu-id="a4704-122">必要なデータを復元できるように、計画を十分にテストしてください。</span><span class="sxs-lookup"><span data-stu-id="a4704-122">Be sure to test your plan thoroughly to be sure you can restore the necessary data.</span></span>  
  
## <a name="configure-remote-partitions"></a><span data-ttu-id="a4704-123">リモート パーティションの構成</span><span class="sxs-lookup"><span data-stu-id="a4704-123">Configure remote partitions</span></span>  
 <span data-ttu-id="a4704-124">のインスタンスを実行している2台の異なるコンピューター [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、1台のコンピューターをマスターサーバーとして、もう一方のコンピューターを下位サーバーとして指定するリモートパーティションの配置を作成するために必要です。</span><span class="sxs-lookup"><span data-stu-id="a4704-124">Two separate computers that are running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] are each required to create a remote partition arrangement that designates one computer as the master server and the other computer as the subordinate server.</span></span>  
  
 <span data-ttu-id="a4704-125">次の手順では、マスター サーバーにキューブ データベースが配置されている、2 つのサーバー インスタンスがあることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a4704-125">The following procedure assumes that you have two server instances, with a cube database deployed on the master server.</span></span> <span data-ttu-id="a4704-126">この手順では、キューブ データベースを db-master と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a4704-126">For the purposes of this procedure, the cube database is referred to as db-master.</span></span> <span data-ttu-id="a4704-127">リモート パーティションが含まれているストレージ データベースを db-storage と呼びます。</span><span class="sxs-lookup"><span data-stu-id="a4704-127">The storage database containing remote partitions is referred to as db-storage.</span></span>  
  
 <span data-ttu-id="a4704-128">この手順を完了するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] と [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="a4704-128">You will use both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to complete this procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4704-129">リモート パーティションとマージできるのは、他のリモート パーティションのみです。</span><span class="sxs-lookup"><span data-stu-id="a4704-129">Remote partitions can be merged only with other remote partitions.</span></span> <span data-ttu-id="a4704-130">ローカル パーティションとリモート パーティションを組み合わせて使用している場合は、別の方法として、結合したデータを含む新しいパーティションを作成し、今後使用しないパーティションを削除する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="a4704-130">If you are using a combination of local and remote partitions, an alternative approach is to create new partitions that include the combined data, deleting the partitions you no longer use.</span></span>  
  
#### <a name="specify-valid-server-names-for-cube-deployment-in-ssdt"></a><span data-ttu-id="a4704-131">キューブの配置に有効なサーバー名を指定する (SSDT)</span><span class="sxs-lookup"><span data-stu-id="a4704-131">Specify valid server names for cube deployment (in SSDT)</span></span>  
  
1.  <span data-ttu-id="a4704-132">マスター サーバー: ソリューション エクスプローラーでソリューション名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4704-132">On the master server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="a4704-133">**[プロパティ]** ダイアログ ボックスで、 **[構成プロパティ]**、 **[配置]**、 **[サーバー]** の順にクリックし、マスター サーバーの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="a4704-133">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the master server's name.</span></span>  
  
2.  <span data-ttu-id="a4704-134">下位サーバー: ソリューション エクスプローラーでソリューション名を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4704-134">On the subordinate server: In Solution Explorer, right-click the solution name and select **Properties**.</span></span> <span data-ttu-id="a4704-135">**[プロパティ]** ダイアログ ボックスで、 **[構成プロパティ]**、 **[配置]**、 **[サーバー]** の順にクリックし、下位サーバーの名前を設定します。</span><span class="sxs-lookup"><span data-stu-id="a4704-135">In the **Properties** dialog box, click **Configuration Properties**, then click **Deployment**, and then click **Server** and set the subordinate server's name.</span></span>  
  
#### <a name="create-and-deploy-a-secondary-database-in-ssdt"></a><span data-ttu-id="a4704-136">セカンダリ データベースを作成および配置する (SSDT)</span><span class="sxs-lookup"><span data-stu-id="a4704-136">Create and deploy a secondary database (in SSDT)</span></span>  
  
1.  <span data-ttu-id="a4704-137">下位サーバー: ストレージ データベース用に新しい Analysis Services プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4704-137">On the subordinate server: Create a new Analysis Services project for the storage database.</span></span>  
  
2.  <span data-ttu-id="a4704-138">下位サーバー: ソリューション エクスプローラーで、キューブ データベース db-master を指す新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4704-138">On the subordinate server: In Solution Explorer, create a new data source pointing to the cube database, db-master.</span></span> <span data-ttu-id="a4704-139">プロバイダーに **[ネイティブ OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="a4704-139">Use the provider **Native OLE DB\Microsoft OLE DB Provider for Analysis Services 11.0**.</span></span>  
  
3.  <span data-ttu-id="a4704-140">下位サーバー: ソリューションを配置します。</span><span class="sxs-lookup"><span data-stu-id="a4704-140">On the subordinate server: Deploy the solution.</span></span>  
  
#### <a name="enable-features-in-ssms"></a><span data-ttu-id="a4704-141">機能を有効にする (SSMS)</span><span class="sxs-lookup"><span data-stu-id="a4704-141">Enable features (in SSMS)</span></span>  
  
1.  <span data-ttu-id="a4704-142">下位サーバー: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、接続している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4704-142">On the subordinate server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="a4704-143">**[機能\LinkToOtherInstanceEnabled]** と **[機能\LinkFromOtherInstanceEnabled]** の両方を **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a4704-143">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
2.  <span data-ttu-id="a4704-144">下位サーバー: オブジェクト エクスプローラーでサーバー名を右クリックして **[再起動]** をクリックし、サーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="a4704-144">On the subordinate server: Restart the server by right-clicking the server name in Object Explorer and selecting **Restart**.</span></span>  
  
3.  <span data-ttu-id="a4704-145">マスター サーバー: [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のオブジェクト エクスプローラーで、接続している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4704-145">On the master server: In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click your connected [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in Object Explorer and select **Properties**.</span></span> <span data-ttu-id="a4704-146">**[機能\LinkToOtherInstanceEnabled]** と **[機能\LinkFromOtherInstanceEnabled]** の両方を **[True]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a4704-146">Set both **Feature\LinkToOtherInstanceEnabled** and **Feature\LinkFromOtherInstanceEnabled** to **True**.</span></span>  
  
4.  <span data-ttu-id="a4704-147">マスター サーバー: オブジェクト エクスプローラーでサーバー名を右クリックして **[再起動]** をクリックし、サーバーを再起動します。</span><span class="sxs-lookup"><span data-stu-id="a4704-147">On the master server: To restart the server, right-click the server name in Object Explorer and select **Restart**.</span></span>  
  
#### <a name="set-the-masterdatasourceid-database-property-on-the-remote-server-in-ssms"></a><span data-ttu-id="a4704-148">リモート サーバーで MasterDataSourceID データベース プロパティを設定する (SSMS)</span><span class="sxs-lookup"><span data-stu-id="a4704-148">Set the MasterDataSourceID database property on the remote server (in SSMS)</span></span>  
  
1.  <span data-ttu-id="a4704-149">下位サーバー: ストレージデータベース db ストレージを右クリックし、[**データベースをスクリプト**化] [  |  **ALTER**  |  **] [新しいクエリエディターウィンドウ]** の順にポイントします。</span><span class="sxs-lookup"><span data-stu-id="a4704-149">On the subordinate server: Right-click the storage database, db-storage, point to **Script Database as** | **ALTER To** | **New Query Editor Window**.</span></span>  
  
2.  <span data-ttu-id="a4704-150">**[MasterDataSourceID]** を XMLA に追加して、キューブ データベース db-master の ID を値として指定します。</span><span class="sxs-lookup"><span data-stu-id="a4704-150">Add **MasterDataSourceID** to the XMLA, and then specify the cube database, db-master, ID as the value.</span></span> <span data-ttu-id="a4704-151">XMLA は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a4704-151">The XMLA should look similar to the following.</span></span>  
  
    ```  
    <Alter ObjectExpansion="ExpandFull" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
    <Object>  
       <DatabaseID>DB-Storage</DatabaseID>  
    </Object>  
    <ObjectDefinition>  
       <Database xmlns:xsd="http://www.w3.org/2001/XMLSchema" 400"   
          <ID>DB-Storage</ID>  
          <Name>DB-StorageB</Name>  
          <ddl200:CompatibilityLevel>1100</ddl200:CompatibilityLevel>  
          <Language>1033</Language>  
          <Collation>Latin1_General_CI_AS</Collation>  
          <DataSourceImpersonationInfo>  
    <ImpersonationMode>ImpersonateAccount</ImpersonationMode>  
             <Account>*********</Account>  
          </DataSourceImpersonationInfo>  
          <MasterDataSourceID>DB-Master</MasterDataSourceID>  
       </Database>  
    </ObjectDefinition>  
    </Alter>  
    ```  
  
3.  <span data-ttu-id="a4704-152">F5 キーを押してスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="a4704-152">Press F5 to execute the script.</span></span>  
  
#### <a name="set-up-the-remote-partition-in-ssdt"></a><span data-ttu-id="a4704-153">リモート パーティションを設定する (SSDT)</span><span class="sxs-lookup"><span data-stu-id="a4704-153">Set up the remote partition (in SSDT)</span></span>  
  
1.  <span data-ttu-id="a4704-154">マスターサーバー: キューブデザイナーでキューブを開き、[**パーティション**] タブをクリックします。メジャーグループを展開します。</span><span class="sxs-lookup"><span data-stu-id="a4704-154">On the master server: Open the cube in Cube Designer and click **Partitions** tab. Expand the measure group.</span></span> <span data-ttu-id="a4704-155">メジャー グループが既に複数のパーティションに対して構成されている場合は **[新しいパーティション]** をクリックします。または、[基になる列] の参照ボタン (.</span><span class="sxs-lookup"><span data-stu-id="a4704-155">Click **New Partition** if the measure group is already configured for multiple partitions, or click the browse (.</span></span> <span data-ttu-id="a4704-156">.</span><span class="sxs-lookup"><span data-stu-id="a4704-156">.</span></span> <span data-ttu-id="a4704-157">) をクリックして既存のパーティションを編集します。</span><span class="sxs-lookup"><span data-stu-id="a4704-157">) button in the Source column to edit the existing partition.</span></span>  
  
2.  <span data-ttu-id="a4704-158">パーティション ウィザードの **[基になる情報の指定]** で、元のデータ ソース ビューとファクト テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="a4704-158">In the Partition Wizard, in **Specify Source Information**, select the original Data Source View and fact table.</span></span>  
  
3.  <span data-ttu-id="a4704-159">クエリ バインドを使用する場合は、作成する新しいパーティションにデータを分割する WHERE 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4704-159">If using a query binding, provide a WHERE clause that segments the data for the new partition you are creating.</span></span>  
  
4.  <span data-ttu-id="a4704-160">**[処理およびストレージの場所]** の **[処理場所]** で、 **[リモート Analysis Services データ ソース]** を選択し、 **[新規作成]** をクリックして、下位データベース db-storage を指す新しいデータ ソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4704-160">In **Processing and Storage Locations**, under **Processing Location**, choose **Remote Analysis Services data source** and click **New** to create a new data source that points to your subordinate database, db-storage.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4704-161">データ ソースがコレクションに存在しないことを示すエラーが発生した場合は、ストレージ データベース db-storage のプロジェクトを開き、master データベース db-master を指すデータ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4704-161">If you get an error indicating the data source does not exist in the collection, you must open the project of the storage database, db-storage, and create a data source that points to the master database, db-master.</span></span>  
  
5.  <span data-ttu-id="a4704-162">マスター サーバー: ソリューション エクスプローラーでキューブ名を右クリックし、 **[処理]** を選択してキューブを完全に処理します。</span><span class="sxs-lookup"><span data-stu-id="a4704-162">On the master server: Right-click the cube name in Solution Explorer, select **Process** and fully process the cube.</span></span>  
  
## <a name="administering-remote-partitions"></a><span data-ttu-id="a4704-163">リモート パーティションの管理</span><span class="sxs-lookup"><span data-stu-id="a4704-163">Administering remote partitions</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a4704-164">は、リモート パーティションの並列処理と順次処理をサポートします。</span><span class="sxs-lookup"><span data-stu-id="a4704-164">supports both parallel and sequential processing of remote partitions.</span></span> <span data-ttu-id="a4704-165">パーティションが定義された master データベースは、キューブのパーティション処理に参加するすべてのインスタンスのトランザクションを調整します。</span><span class="sxs-lookup"><span data-stu-id="a4704-165">The master database, where the partitions were defined, coordinates the transactions among all the instances that participate in processing the partitions of a cube.</span></span> <span data-ttu-id="a4704-166">処理のレポートは、パーティションを処理するすべてのインスタンスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="a4704-166">Processing reports are then sent to all instances that processed a partition.</span></span>  
  
 <span data-ttu-id="a4704-167">リモート パーティションを含むキューブは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の 1 つのインスタンスでそのパーティションと共に管理されます。</span><span class="sxs-lookup"><span data-stu-id="a4704-167">A cube that contains remote partitions can be administered together with its partitions on a single instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a4704-168">ただし、リモート パーティションのメタデータは、パーティションとその親キューブが定義された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスでのみ表示および更新できます。</span><span class="sxs-lookup"><span data-stu-id="a4704-168">However, the metadata for the remote partition can be viewed and updated only on the instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] where the partition and its parent cube were defined.</span></span> <span data-ttu-id="a4704-169">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のリモート インスタンスではリモート パーティションを表示または更新できません。</span><span class="sxs-lookup"><span data-stu-id="a4704-169">The remote partition cannot be viewed or updated on the remote instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4704-170">リモート パーティションの格納専用のデータベースは、スキーマ行セットに対して公開されていませんが、分析管理オブジェクト (AMO) を使用するアプリケーションは、Analysis Discover コマンドの XML を使用して専用データベースを検出できます。</span><span class="sxs-lookup"><span data-stu-id="a4704-170">Although databases dedicated to storage of remote partitions are not exposed to schema rowsets, applications that use Analysis Management Objects (AMO) can still discover a dedicated database by using the XML for Analysis Discover command.</span></span> <span data-ttu-id="a4704-171">TCP または HTTP クライアントを使用して専用データベースに直接送信された CREATE コマンドまたは DELETE コマンドは成功しますが、操作によりこの厳密管理データベースが損傷する可能性があることを示す警告がサーバーにより返されます。</span><span class="sxs-lookup"><span data-stu-id="a4704-171">Any CREATE or DELETE command that is sent directly to a dedicated database by using a TCP or HTTP client will succeed, but the server will return a warning indicating that the action may damage this closely managed database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4704-172">参照</span><span class="sxs-lookup"><span data-stu-id="a4704-172">See Also</span></span>  
 [<span data-ttu-id="a4704-173">パーティション (Analysis Services - 多次元データ)</span><span class="sxs-lookup"><span data-stu-id="a4704-173">Partitions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)  
  
  
