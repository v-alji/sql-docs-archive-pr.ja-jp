---
title: MSSQLSERVER_2570 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2570 (Database Engine error)
ms.assetid: 29800aa9-81aa-4371-992c-487dbb617f46
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 79137d0f70c05c6aa7b758f7e073d152681a14b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713189"
---
# <a name="mssqlserver_2570"></a><span data-ttu-id="46a15-102">MSSQLSERVER_2570</span><span class="sxs-lookup"><span data-stu-id="46a15-102">MSSQLSERVER_2570</span></span>
    
## <a name="details"></a><span data-ttu-id="46a15-103">詳細</span><span class="sxs-lookup"><span data-stu-id="46a15-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46a15-104">製品名</span><span class="sxs-lookup"><span data-stu-id="46a15-104">Product Name</span></span>|<span data-ttu-id="46a15-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="46a15-105">SQL Server</span></span>|  
|<span data-ttu-id="46a15-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="46a15-106">Event ID</span></span>|<span data-ttu-id="46a15-107">2570</span><span class="sxs-lookup"><span data-stu-id="46a15-107">2570</span></span>|  
|<span data-ttu-id="46a15-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="46a15-108">Event Source</span></span>|<span data-ttu-id="46a15-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="46a15-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="46a15-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="46a15-110">Component</span></span>|<span data-ttu-id="46a15-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="46a15-111">SQLEngine</span></span>|  
|<span data-ttu-id="46a15-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="46a15-112">Symbolic Name</span></span>|<span data-ttu-id="46a15-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span><span class="sxs-lookup"><span data-stu-id="46a15-113">DBCC_COLUMN_VALUE_OUT_OF_RANGE</span></span>|  
|<span data-ttu-id="46a15-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="46a15-114">Message Text</span></span>|<span data-ttu-id="46a15-115">ページ P_ID、オブジェクト ID O_ID のスロット S_ID、インデックス ID I_ID、パーティション ID PN_ID、アロケーション ユニット ID A_ID (型 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="46a15-115">Page P_ID, slot S_ID in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="46a15-116">列 COLUMN_NAME の値が、データ型 "DATATYPE" の範囲外です。</span><span class="sxs-lookup"><span data-stu-id="46a15-116">Column COLUMN_NAME value is out of range for data type "DATATYPE".</span></span> <span data-ttu-id="46a15-117">列を有効な値に更新してください。</span><span class="sxs-lookup"><span data-stu-id="46a15-117">Update column to a legal value.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="46a15-118">説明</span><span class="sxs-lookup"><span data-stu-id="46a15-118">Explanation</span></span>  
 <span data-ttu-id="46a15-119">指定した列に格納されている値は、列のデータ型に対する有効値の範囲外です。</span><span class="sxs-lookup"><span data-stu-id="46a15-119">The column value that is contained in the specified column is outside the range of possible values for the column data type.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="46a15-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="46a15-120">User Action</span></span>  
 <span data-ttu-id="46a15-121">このエラーは修復できません。</span><span class="sxs-lookup"><span data-stu-id="46a15-121">The error is not repairable.</span></span> <span data-ttu-id="46a15-122">列のデータ型に対する範囲内に収まるよう列の値を更新して、再度コマンドを実行してください。</span><span class="sxs-lookup"><span data-stu-id="46a15-122">Update the column to a value within the range for the data type of the column and run the command again.</span></span>  <span data-ttu-id="46a15-123">詳細については、サポート技術情報の資料 [923247](https://support.microsoft.com/kb/923247) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46a15-123">For more information, see this KB article [923247](https://support.microsoft.com/kb/923247).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46a15-124">参照</span><span class="sxs-lookup"><span data-stu-id="46a15-124">See Also</span></span>  
 <span data-ttu-id="46a15-125">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="46a15-125">[UPDATE &#40;Transact-SQL&#41;](/sql/t-sql/queries/update-transact-sql) </span></span>  
 [<span data-ttu-id="46a15-126">データ型 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="46a15-126">Data Types &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
  
