---
title: MSSQLSERVER_1793 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 808db1d0-acc1-41d0-9287-8a5455001a02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54172adb957c3cbc1dbc221d1cae2a583830a1cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715349"
---
# <a name="mssqlserver_1793"></a><span data-ttu-id="91f5f-102">MSSQLSERVER_1793</span><span class="sxs-lookup"><span data-stu-id="91f5f-102">MSSQLSERVER_1793</span></span>
    
## <a name="details"></a><span data-ttu-id="91f5f-103">詳細</span><span class="sxs-lookup"><span data-stu-id="91f5f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91f5f-104">製品名</span><span class="sxs-lookup"><span data-stu-id="91f5f-104">Product Name</span></span>|<span data-ttu-id="91f5f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="91f5f-105">SQL Server</span></span>|  
|<span data-ttu-id="91f5f-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="91f5f-106">Event ID</span></span>|<span data-ttu-id="91f5f-107">1793</span><span class="sxs-lookup"><span data-stu-id="91f5f-107">1793</span></span>|  
|<span data-ttu-id="91f5f-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="91f5f-108">Event Source</span></span>|<span data-ttu-id="91f5f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="91f5f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="91f5f-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="91f5f-110">Component</span></span>|<span data-ttu-id="91f5f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="91f5f-111">SQLEngine</span></span>|  
|<span data-ttu-id="91f5f-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="91f5f-112">Symbolic Name</span></span>|<span data-ttu-id="91f5f-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span><span class="sxs-lookup"><span data-stu-id="91f5f-113">FILESTREAM_BASEDATA_NEED_SAME_PARTITION</span></span>|  
|<span data-ttu-id="91f5f-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="91f5f-114">Message Text</span></span>|<span data-ttu-id="91f5f-115">パーティション構成が FILESTREAM データに指定されていないため、操作 (インデックス '%.\*ls' の削除) を実行できません。</span><span class="sxs-lookup"><span data-stu-id="91f5f-115">Cannot drop index '%.\*ls' since a partition scheme is not specified for FILESTREAM data.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="91f5f-116">説明</span><span class="sxs-lookup"><span data-stu-id="91f5f-116">Explanation</span></span>  
 <span data-ttu-id="91f5f-117">このメッセージは、FILESTREAM データを含むテーブルで、クラスター化インデックスの削除を実行する場合に、基本データに **MOVE TO** 句を指定したにもかかわらず、FILESTREAM データに **FILESTREAM_ON** 句が指定されていないときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="91f5f-117">This message occurs when you try to drop a clustered index on a table that contains FILESTREAM data, and you specify a **MOVE TO** clause for the base data, but you do not specify a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="91f5f-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="91f5f-118">User Action</span></span>  
 <span data-ttu-id="91f5f-119">FILESTREAM データを含むテーブルで、クラスター化インデックスを削除する場合は、次のオプションのどちらかを使用します。</span><span class="sxs-lookup"><span data-stu-id="91f5f-119">When dropping a clustered index on a table that contains FILESTREAM data, use one of the following options:</span></span>  
  
-   <span data-ttu-id="91f5f-120">基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方を指定します。</span><span class="sxs-lookup"><span data-stu-id="91f5f-120">Specify both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
-   <span data-ttu-id="91f5f-121">基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方とも指定しません。</span><span class="sxs-lookup"><span data-stu-id="91f5f-121">Do not specify either a **MOVE TO** clause for the base data or a **FILESTREAM_ON** clause for the FILESTREAM data.</span></span>  
  
 <span data-ttu-id="91f5f-122">次の例は、基本データにパーティション構成が指定されているにもかかわらず、FILESTREAM データには指定されているので、失敗します。</span><span class="sxs-lookup"><span data-stu-id="91f5f-122">The following example fails because a partition scheme is specified for the base data, but is not specified for the FILESTREAM data.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY] )  
GO  
```  
  
 <span data-ttu-id="91f5f-123">次の例は、基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方が指定されているので、成功します。</span><span class="sxs-lookup"><span data-stu-id="91f5f-123">The following example succeeds because both a **MOVE TO** clause for the base data and a **FILESTREAM_ON** clause for the FILESTREAM data are specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF, MOVE TO [PRIMARY], filestream_on 'default' )  
GO  
```  
  
 <span data-ttu-id="91f5f-124">次の例は、基本データに **MOVE TO** 句、FILESTREAM データに **FILESTREAM_ON** 句の両方とも指定されていないので、成功します。</span><span class="sxs-lookup"><span data-stu-id="91f5f-124">The following example also succeeds because neither a **MOVE TO** clause for the base data nor a **FILESTREAM_ON** clause for the FILESTREAM data is specified.</span></span>  
  
```sql  
DROP INDEX [<clustered_index_name>] ON [<table_name>]   
WITH ( ONLINE = OFF )  
GO  
```  
  
  
