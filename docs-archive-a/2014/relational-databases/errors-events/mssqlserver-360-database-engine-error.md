---
title: MSSQLSERVER_360 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b30311d7f55231c1e7a6d5969d49c5d1bc07a848
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639539"
---
# <a name="mssqlserver_360"></a><span data-ttu-id="8fbea-102">MSSQLSERVER_360</span><span class="sxs-lookup"><span data-stu-id="8fbea-102">MSSQLSERVER_360</span></span>
    
## <a name="details"></a><span data-ttu-id="8fbea-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8fbea-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8fbea-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8fbea-104">Product Name</span></span>|<span data-ttu-id="8fbea-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8fbea-105">SQL Server</span></span>|  
|<span data-ttu-id="8fbea-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8fbea-106">Event ID</span></span>|<span data-ttu-id="8fbea-107">360</span><span class="sxs-lookup"><span data-stu-id="8fbea-107">360</span></span>|  
|<span data-ttu-id="8fbea-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8fbea-108">Event Source</span></span>|<span data-ttu-id="8fbea-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8fbea-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8fbea-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8fbea-110">Component</span></span>|<span data-ttu-id="8fbea-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8fbea-111">SQLEngine</span></span>|  
|<span data-ttu-id="8fbea-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8fbea-112">Symbolic Name</span></span>|<span data-ttu-id="8fbea-113">DML_UPDATE_SPARSE_AND_COLSET</span><span class="sxs-lookup"><span data-stu-id="8fbea-113">DML_UPDATE_SPARSE_AND_COLSET</span></span>|  
|<span data-ttu-id="8fbea-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8fbea-114">Message Text</span></span>|<span data-ttu-id="8fbea-115">INSERT、UPDATE、または MERGE ステートメントの対象の列リストには、スパース列と、スパース列を含む列セットの両方を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="8fbea-115">The target column list of an INSERT, UPDATE, or MERGE statement cannot contain both a sparse column and the column set that contains the sparse column.</span></span> <span data-ttu-id="8fbea-116">スパース列と列セットの両方ではなく、いずれかを含めるようにステートメントを書き直してください。</span><span class="sxs-lookup"><span data-stu-id="8fbea-116">Rewrite the statement to include either the sparse column or the column set, but not both.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8fbea-117">説明</span><span class="sxs-lookup"><span data-stu-id="8fbea-117">Explanation</span></span>  
 <span data-ttu-id="8fbea-118">列セットは、型指定されていない XML 表現であり、テーブルの複数の列を 1 つにまとめて構造化した出力です。</span><span class="sxs-lookup"><span data-stu-id="8fbea-118">A column set is an untyped XML representation that combines some columns of a table into a structured output.</span></span> <span data-ttu-id="8fbea-119">列セットと、列セットに含まれる列の両方を変更しようとして、同じ列への参照が 2 つ発生しました。</span><span class="sxs-lookup"><span data-stu-id="8fbea-119">An attempt was made to modify both the column set and a column that is included in the column set, causing two references to the same column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8fbea-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8fbea-120">User Action</span></span>  
 <span data-ttu-id="8fbea-121">列または列セットのいずれかへの参照を含めるようにステートメントを書き直して、両方をステートメントに含めないでください。</span><span class="sxs-lookup"><span data-stu-id="8fbea-121">Rewrite the statement to include references to either the column or the column set, but do not include both in the statement.</span></span>  
  
  
