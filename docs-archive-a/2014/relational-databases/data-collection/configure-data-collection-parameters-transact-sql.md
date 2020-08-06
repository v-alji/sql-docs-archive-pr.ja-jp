---
title: データ コレクションのパラメーターの構成 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a8333b47612b4fbd933ef132e886b8125ffb58a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718261"
---
# <a name="configure-data-collection-parameters-transact-sql"></a><span data-ttu-id="0442b-102">データ コレクションのパラメーターの構成 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="0442b-102">Configure Data Collection Parameters (Transact-SQL)</span></span>
  <span data-ttu-id="0442b-103">カスタム コレクション セットを作成する前に、データ コレクションのパラメーターを構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0442b-103">Before you create a custom collection set, you must first configure data collection parameters.</span></span> <span data-ttu-id="0442b-104">これには、データ コレクターで用意されているストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="0442b-104">You can do this by using the stored procedures that are provided with the data collector.</span></span> <span data-ttu-id="0442b-105">この作業には、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のクエリ エディターを使用した次の手順の実行も含まれます。</span><span class="sxs-lookup"><span data-stu-id="0442b-105">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0442b-106">データ コレクションのパラメーターは一度構成するだけです。</span><span class="sxs-lookup"><span data-stu-id="0442b-106">You only configure data collection parameters once.</span></span> <span data-ttu-id="0442b-107">構成後に作成した追加のコレクション セットには、すべてこれらのパラメーターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0442b-107">After configuration, these parameters are used for any additional collection sets that you create.</span></span>  
  
### <a name="configure-data-collection-parameters"></a><span data-ttu-id="0442b-108">データ コレクションのパラメーターの構成</span><span class="sxs-lookup"><span data-stu-id="0442b-108">Configure data collection parameters</span></span>  
  
1.  <span data-ttu-id="0442b-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、カスタム コレクション セットを作成するデータベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="0442b-109">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to the database where you want to create a custom collection set.</span></span>  
  
2.  <span data-ttu-id="0442b-110">クエリ エディターで、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="0442b-110">In Query Editor, issue the following statements.</span></span>  
  
    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0442b-111">参照</span><span class="sxs-lookup"><span data-stu-id="0442b-111">See Also</span></span>  
 <span data-ttu-id="0442b-112">[[データ コレクション]](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="0442b-112">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="0442b-113">データ コレクター ストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0442b-113">Data Collector Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
