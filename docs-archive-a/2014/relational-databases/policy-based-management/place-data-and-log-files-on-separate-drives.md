---
title: 別々のドライブへのデータ ファイルとログ ファイルの配置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 6cbedc27-4d77-44ad-bed2-c23b628475a7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d3f972ea29322a046c09657e2ed2499655c82aed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642731"
---
# <a name="place-data-and-log-files-on-separate-drives"></a><span data-ttu-id="7e93b-102">別々のドライブへのデータ ファイルとログ ファイルの配置</span><span class="sxs-lookup"><span data-stu-id="7e93b-102">Place Data and Log Files on Separate Drives</span></span>
  <span data-ttu-id="7e93b-103">このルールでは、データ ファイルとログ ファイルが別々の論理ドライブに配置されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7e93b-103">This rule checks whether data and log files are placed on separate logical drives.</span></span> <span data-ttu-id="7e93b-104">データ ファイルとログ ファイルの両方を同じデバイスに配置すると、そのデバイスで競合が発生し、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7e93b-104">Placing both data and log files on the same device can cause contention for that device and result in poor performance.</span></span> <span data-ttu-id="7e93b-105">ファイルを別々のドライブに配置すると、I/O 動作をデータ ファイルとログ ファイルの両方で同時に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7e93b-105">Placing the files on separate drives allows the I/O activity to occur at the same time for both the data and log files.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="7e93b-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="7e93b-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="7e93b-107">新しいデータベースを作成するときに、データ用とログ用に別々のドライブを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e93b-107">When you create a new database, specify separate drives for the data and log.</span></span> <span data-ttu-id="7e93b-108">データベースの作成後にファイルを移動するには、データベースをオフラインにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e93b-108">To move files after the database is created, the database must be taken offline.</span></span> <span data-ttu-id="7e93b-109">次のいずれかの方法を使用して、ファイルを移動します。</span><span class="sxs-lookup"><span data-stu-id="7e93b-109">Move the files by using one of the following methods:</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7e93b-110">このポリシーでは、マウント ポイントを介して別個の物理デバイスを検出することはできません。</span><span class="sxs-lookup"><span data-stu-id="7e93b-110">This policy cannot detect separate physical devices through mount points</span></span>  
  
-   <span data-ttu-id="7e93b-111">RESTORE DATABASE ステートメントで WITH MOVE オプションを使用してバックアップからデータベースを復元します。</span><span class="sxs-lookup"><span data-stu-id="7e93b-111">Restore the database from backup by using the RESTORE DATABASE statement with the WITH MOVE option.</span></span>  
  
-   <span data-ttu-id="7e93b-112">データベースをデタッチしてから、データ デバイス用とログ デバイス用に別々の場所を指定してデータベースをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="7e93b-112">Detach and then attach the database specifying separate locations for the data and log devices.</span></span>  
  
-   <span data-ttu-id="7e93b-113">MODIFY FILE オプションを指定して ALTER DATABASE ステートメントを実行し、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスを再起動して、新しい場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="7e93b-113">Specify a new location by running the ALTER DATABASE statement with the MODIFY FILE option, and then restarting the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="7e93b-114">詳細情報</span><span class="sxs-lookup"><span data-stu-id="7e93b-114">For More Information</span></span>  
 [<span data-ttu-id="7e93b-115">データベース ファイルの移動</span><span class="sxs-lookup"><span data-stu-id="7e93b-115">Move Database Files</span></span>](../databases/move-database-files.md)  
  
 [<span data-ttu-id="7e93b-116">ユーザー データベースの移動</span><span class="sxs-lookup"><span data-stu-id="7e93b-116">Move User Databases</span></span>](../databases/move-user-databases.md)  
  
 [<span data-ttu-id="7e93b-117">データベースのデタッチとアタッチ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="7e93b-117">Database Detach and Attach &#40;SQL Server&#41;</span></span>](../databases/database-detach-and-attach-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="7e93b-118">参照</span><span class="sxs-lookup"><span data-stu-id="7e93b-118">See Also</span></span>  
 [<span data-ttu-id="7e93b-119">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="7e93b-119">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
