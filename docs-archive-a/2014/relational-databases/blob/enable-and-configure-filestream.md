---
title: FILESTREAM の有効化と構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], enabling
ms.assetid: 78737e19-c65b-48d9-8fa9-aa6f1e1bce73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f6c0e505bd32636d045519b36e439bc21c7079d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631105"
---
# <a name="enable-and-configure-filestream"></a><span data-ttu-id="3b1c1-102">FILESTREAM の有効化と構成</span><span class="sxs-lookup"><span data-stu-id="3b1c1-102">Enable and Configure FILESTREAM</span></span>
  <span data-ttu-id="3b1c1-103">FILESTREAM の使用を開始するには、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]のインスタンスで FILESTREAM を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-103">Before you can start to use FILESTREAM, you must enable FILESTREAM on the instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="3b1c1-104">このトピックでは、SQL Server 構成マネージャーを使用して FILESTREAM を有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-104">This topic describes how to enable FILESTREAM by using SQL Server Configuration Manager.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3b1c1-105">64 ビット オペレーティング システム上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の 32 ビット バージョンでは FILESTREAM を有効にできません。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-105">You cannot enable FILESTREAM on a 32-bit version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on a 64-bit operating system.</span></span>  
  
##  <a name="enabling-filestream"></a><a name="enabling"></a> <span data-ttu-id="3b1c1-106">FILESTREAM の有効化</span><span class="sxs-lookup"><span data-stu-id="3b1c1-106">Enabling FILESTREAM</span></span>  
  
#### <a name="to-enable-and-change-filestream-settings"></a><span data-ttu-id="3b1c1-107">FILESTREAM の設定の有効化と変更</span><span class="sxs-lookup"><span data-stu-id="3b1c1-107">To enable and change FILESTREAM settings</span></span>  
  
1.  <span data-ttu-id="3b1c1-108">**[スタート]** メニューで、 **[すべてのプログラム]** 、[ [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]]、 **[構成ツール]** の順にポイントして、 **[SQL Server 構成マネージャー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-108">On the **Start** menu, point to **All Programs**, point to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], point to **Configuration Tools**, and then click **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="3b1c1-109">サービスの一覧で、 **[SQL Server のサービス]** を右クリックし、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-109">In the list of services, right-click **SQL Server Services**, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="3b1c1-110">**[SQL Server 構成マネージャー]** スナップインで、FILESTREAM を有効にする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを探します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-110">In the **SQL Server Configuration Manager** snap-in, locate the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on which you want to enable FILESTREAM.</span></span>  
  
4.  <span data-ttu-id="3b1c1-111">インスタンスを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-111">Right-click the instance, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="3b1c1-112">**[SQL Server のプロパティ]** ダイアログ ボックスで、 **[FILESTREAM]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-112">In the **SQL Server Properties** dialog box, click the **FILESTREAM** tab.</span></span>  
  
6.  <span data-ttu-id="3b1c1-113">**[Transact-SQL アクセスに対して FILESTREAM を有効にする]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-113">Select the **Enable FILESTREAM for Transact-SQL access** check box.</span></span>  
  
7.  <span data-ttu-id="3b1c1-114">Windows から FILESTREAM データの読み取りと書き込みを行う場合は、 **[ファイル I/O ストリーム アクセスに対して FILESTREAM を有効にする]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-114">If you want to read and write FILESTREAM data from Windows, click **Enable FILESTREAM for file I/O streaming access**.</span></span> <span data-ttu-id="3b1c1-115">Windows 共有の名前を **[Windows 共有名]** ボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-115">Enter the name of the Windows share in the **Windows Share Name** box.</span></span>  
  
8.  <span data-ttu-id="3b1c1-116">この共有に格納された FILESTREAM データにリモート クライアントからアクセスする必要がある場合は、 **[リモート クライアントに FILESTREAM データへのストリーム アクセスを許可する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-116">If remote clients must access the FILESTREAM data that is stored on this share, select **Allow remote clients to have streaming access to FILESTREAM data**.</span></span>  
  
9. <span data-ttu-id="3b1c1-117">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-117">Click **Apply**.</span></span>  
  
10. <span data-ttu-id="3b1c1-118">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[新しいクエリ]** をクリックしてクエリ エディターを表示します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], click **New Query** to display the Query Editor.</span></span>  
  
11. <span data-ttu-id="3b1c1-119">クエリ エディターで、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを入力します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-119">In Query Editor, enter the following [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
    ```sql  
    EXEC sp_configure filestream_access_level, 2  
    RECONFIGURE  
    ```  
  
12. <span data-ttu-id="3b1c1-120">**[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-120">Click **Execute**.</span></span>  
  
13. <span data-ttu-id="3b1c1-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスを再開します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-121">Restart the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service.</span></span>  
  

  
##  <a name="best-practices"></a><a name="best"></a> <span data-ttu-id="3b1c1-122">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="3b1c1-122">Best Practices</span></span>  
  
###  <a name="physical-configuration-and-maintenance"></a><a name="config"></a><span data-ttu-id="3b1c1-123">物理的な構成とメンテナンス</span><span class="sxs-lookup"><span data-stu-id="3b1c1-123">Physical Configuration and Maintenance</span></span>  
 <span data-ttu-id="3b1c1-124">FILESTREAM ストレージ ボリュームを設定する場合は、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-124">When you set up FILESTREAM storage volumes, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="3b1c1-125">FILESTREAM コンピューター システム上で短いファイル名を無効にします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-125">Turn off short file names on FILESTREAM computer systems.</span></span> <span data-ttu-id="3b1c1-126">短いファイル名の作成には、長い時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-126">Short file names take significantly longer to create.</span></span> <span data-ttu-id="3b1c1-127">短いファイル名を無効にするには、Windows **fsutil** ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-127">To disable short file names, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="3b1c1-128">FILESTREAM コンピューター システムを定期的に最適化します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-128">Regularly defragment FILESTREAM computer systems.</span></span>  
  
-   <span data-ttu-id="3b1c1-129">64 KB の NTFS クラスターを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-129">Use 64-KB NTFS clusters.</span></span> <span data-ttu-id="3b1c1-130">圧縮されたボリュームは、4 KB の NTFS クラスターに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-130">Compressed volumes must be set to 4-KB NTFS clusters.</span></span>  
  
-   <span data-ttu-id="3b1c1-131">FILESTREAM ボリューム上のインデックスの作成を無効にし、 **disablelastaccess** を設定します。 **disablelastaccess**を設定するには、Windows **fsutil** ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-131">Disable indexing on FILESTREAM volumes and set **disablelastaccess** To set **disablelastaccess**, use the Windows **fsutil** utility.</span></span>  
  
-   <span data-ttu-id="3b1c1-132">必要でない場合は、FILESTREAM ボリューム上でのウイルス スキャンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-132">Disable antivirus scanning of FILESTREAM volumes when it is not unnecessary.</span></span> <span data-ttu-id="3b1c1-133">ウイルス スキャンが必要な場合は、問題のあるファイルを自動的に削除するポリシーを設定しないようにします。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-133">If antivirus scanning is necessary, avoid setting policies that will automatically delete offending files.</span></span>  
  
-   <span data-ttu-id="3b1c1-134">RAID レベルを設定および調整して、フォールト トレランスとアプリケーションで求められるパフォーマンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-134">Set up and tune the RAID level for fault tolerance and the performance that is required by an application.</span></span>  
  
||||||  
|-|-|-|-|-|  
|<span data-ttu-id="3b1c1-135">RAID レベル</span><span class="sxs-lookup"><span data-stu-id="3b1c1-135">RAID level</span></span>|<span data-ttu-id="3b1c1-136">書き込みパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="3b1c1-136">Write performance</span></span>|<span data-ttu-id="3b1c1-137">読み取りパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="3b1c1-137">Read performance</span></span>|<span data-ttu-id="3b1c1-138">フォールト トレランス</span><span class="sxs-lookup"><span data-stu-id="3b1c1-138">Fault tolerance</span></span>|<span data-ttu-id="3b1c1-139">解説</span><span class="sxs-lookup"><span data-stu-id="3b1c1-139">Remarks</span></span>|  
|<span data-ttu-id="3b1c1-140">RAID 5</span><span class="sxs-lookup"><span data-stu-id="3b1c1-140">RAID 5</span></span>|<span data-ttu-id="3b1c1-141">Normal</span><span class="sxs-lookup"><span data-stu-id="3b1c1-141">Normal</span></span>|<span data-ttu-id="3b1c1-142">Normal</span><span class="sxs-lookup"><span data-stu-id="3b1c1-142">Normal</span></span>|<span data-ttu-id="3b1c1-143">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="3b1c1-143">Excellent</span></span>|<span data-ttu-id="3b1c1-144">パフォーマンスは、1 台のディスクまたは JBOD よりも高く、RAID 0 またはストライピング機能を備えた RAID 5 よりも低くなります。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-144">Performance is better than one disk or JBOD; and less than RAID 0 or RAID 5 with striping.</span></span>|  
|<span data-ttu-id="3b1c1-145">RAID 0</span><span class="sxs-lookup"><span data-stu-id="3b1c1-145">RAID 0</span></span>|<span data-ttu-id="3b1c1-146">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="3b1c1-146">Excellent</span></span>|<span data-ttu-id="3b1c1-147">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="3b1c1-147">Excellent</span></span>|<span data-ttu-id="3b1c1-148">なし</span><span class="sxs-lookup"><span data-stu-id="3b1c1-148">None</span></span>||  
|<span data-ttu-id="3b1c1-149">RAID 5 + ストライピング</span><span class="sxs-lookup"><span data-stu-id="3b1c1-149">RAID 5 + stripping</span></span>|<span data-ttu-id="3b1c1-150">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="3b1c1-150">Excellent</span></span>|<span data-ttu-id="3b1c1-151">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="3b1c1-151">Excellent</span></span>|<span data-ttu-id="3b1c1-152">[非常に良い]</span><span class="sxs-lookup"><span data-stu-id="3b1c1-152">Excellent</span></span>|<span data-ttu-id="3b1c1-153">最も高価なオプションです。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-153">Most expensive option.</span></span>|  
  

  
###  <a name="physical-database-design"></a><a name="database"></a><span data-ttu-id="3b1c1-154">物理的なデータベース設計</span><span class="sxs-lookup"><span data-stu-id="3b1c1-154">Physical Database Design</span></span>  
 <span data-ttu-id="3b1c1-155">FILESTREAM データベースを設計するときは、次のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-155">When you design a FILESTREAM database, consider the following guidelines:</span></span>  
  
-   <span data-ttu-id="3b1c1-156">FILESTREAM 列には、対応する ROWGUID 列が指定されている必要があり `uniqueidentifier` ます。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-156">FILESTREAM columns must be accompanied by a corresponding `uniqueidentifier`ROWGUID column.</span></span> <span data-ttu-id="3b1c1-157">また、この種のテーブルには、一意なインデックスが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-157">These kinds of tables must also be accompanied by a unique index.</span></span> <span data-ttu-id="3b1c1-158">通常、このインデックスは、クラスター化インデックスではありません。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-158">Typically this index is not a clustered index.</span></span> <span data-ttu-id="3b1c1-159">データベースのビジネス ロジックでクラスター化インデックスが求められる場合は、インデックスに格納されている値がランダムでないことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-159">If the databases business logic requires a clustered index, you have to make sure that the values stored in the index are not random.</span></span> <span data-ttu-id="3b1c1-160">格納されている値がランダムである場合、テーブルの行が追加または削除されるたびにインデックスの並べ替えが発生します。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-160">Random values will cause the index to be reordered every time that a row is added or removed from the table.</span></span>  
  
-   <span data-ttu-id="3b1c1-161">パフォーマンス上の理由から、FILESTREAM ファイル グループおよびコンテナーは、オペレーティング システム、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログ、tempdb、ページング ファイル以外のボリュームに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-161">For performance reasons, FILESTREAM filegroups and containers should reside on volumes other than the operating system, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] log, tempdb, or paging file.</span></span>  
  
-   <span data-ttu-id="3b1c1-162">領域管理とポリシーは、FILESTREAM では直接サポートされません。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-162">Space management and policies are not directly supported by FILESTREAM.</span></span> <span data-ttu-id="3b1c1-163">ただし、それぞれの FILESTREAM ファイル グループを別個のボリュームに割り当て、ボリュームの管理機能を使用することで、領域の管理とポリシーの適用を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="3b1c1-163">However, you can manage space and apply policies indirectly by assigning each FILESTREAM filegroup to a separate volume and using the volume's management features.</span></span>  
  
  
