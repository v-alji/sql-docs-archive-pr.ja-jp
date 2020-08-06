---
title: ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c2c6f050-8cdb-4b8e-ad38-4aae0a949847
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 60b9623b468f2763cf619c325412373e3603f3a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633148"
---
# <a name="configure-your-utility-control-point-data-warehouse-sql-server-utility"></a><span data-ttu-id="24ac8-102">ユーティリティ コントロール ポイント データ ウェアハウスの構成 (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="24ac8-102">Configure Your Utility Control Point Data Warehouse (SQL Server Utility)</span></span>
  <span data-ttu-id="24ac8-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のマネージド インスタンスで収集されたデータは、ユーティリティ管理データ ウェアハウス (UMDW) に格納されます。UMDW ファイル名は sysutility_mdw です。</span><span class="sxs-lookup"><span data-stu-id="24ac8-103">Data collected by managed instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are stored in the utility management data warehouse (UMDW); the UMDW file name is sysutility_mdw.</span></span>  
  
 <span data-ttu-id="24ac8-104">UMDW のデータ保持期間を構成できます。</span><span class="sxs-lookup"><span data-stu-id="24ac8-104">You can configure the UMDW data retention period.</span></span> <span data-ttu-id="24ac8-105">詳細については、「[ユーティリティの管理 &#40;SQL Server ユーティリティ&#41;](../../database-engine/utility-administration-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24ac8-105">For more information, see [Utility Administration &#40;SQL Server Utility&#41;](../../database-engine/utility-administration-sql-server-utility.md).</span></span>  
  
 <span data-ttu-id="24ac8-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこのリリースで構成できない構成設定は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="24ac8-106">The following configuration settings are not configurable in this release of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="24ac8-107">UMDW 名: Sysutility_mdw。</span><span class="sxs-lookup"><span data-stu-id="24ac8-107">UMDW name: Sysutility_mdw.</span></span>  
  
-   <span data-ttu-id="24ac8-108">コレクション セットのアップロードの頻度: 15 分ごと。</span><span class="sxs-lookup"><span data-stu-id="24ac8-108">Collection set upload frequency: Every 15 minutes.</span></span>  
  
 <span data-ttu-id="24ac8-109">UMDW ディレクトリ \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\ (通常、\<System drive> は C:\ ドライブ) は構成可能です。</span><span class="sxs-lookup"><span data-stu-id="24ac8-109">The UMDW directory is configurable: \<System drive>:\Program Files\Microsoft SQL Server\MSSQL10_50.<UCP_Name>\MSSQL\Data\\, where \<System drive> is normally the C:\ drive.</span></span> <span data-ttu-id="24ac8-110">ログ ファイル Sysutility_mdw_\<GUID>_LOG は同じディレクトリにあります。</span><span class="sxs-lookup"><span data-stu-id="24ac8-110">The log file, Sysutility_mdw_\<GUID>_LOG, is located in the same directory.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="24ac8-111">UMDW (sysutility_mdw) ファイルの場所を変更するには、デタッチとアタッチを使用する方法と ALTER DATABASE を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="24ac8-111">The UMDW (sysutility_mdw) file location can be changed using detach/attach or ALTER DATABASE.</span></span> <span data-ttu-id="24ac8-112">ALTER DATABASE の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="24ac8-112">We recommend the use of ALTER DATABASE.</span></span> <span data-ttu-id="24ac8-113">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24ac8-113">For more information see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24ac8-114">参照</span><span class="sxs-lookup"><span data-stu-id="24ac8-114">See Also</span></span>  
 [<span data-ttu-id="24ac8-115">SQL Server ユーティリティの機能とタスク</span><span class="sxs-lookup"><span data-stu-id="24ac8-115">SQL Server Utility Features and Tasks</span></span>](sql-server-utility-features-and-tasks.md)  
  
  
