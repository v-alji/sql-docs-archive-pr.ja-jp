---
title: MSSQLSERVER_11409 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 11409 (Database Engine error)
ms.assetid: 99b71a1c-a72d-4ca9-9d00-4230c9042ba5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e4249e13a3530f69978c78f2e2ca6e4583eed46a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631995"
---
# <a name="mssqlserver_11409"></a><span data-ttu-id="05b59-102">MSSQLSERVER_11409</span><span class="sxs-lookup"><span data-stu-id="05b59-102">MSSQLSERVER_11409</span></span>
    
## <a name="details"></a><span data-ttu-id="05b59-103">詳細</span><span class="sxs-lookup"><span data-stu-id="05b59-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05b59-104">製品名</span><span class="sxs-lookup"><span data-stu-id="05b59-104">Product Name</span></span>|<span data-ttu-id="05b59-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="05b59-105">SQL Server</span></span>|  
|<span data-ttu-id="05b59-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="05b59-106">Event ID</span></span>|<span data-ttu-id="05b59-107">11409</span><span class="sxs-lookup"><span data-stu-id="05b59-107">11409</span></span>|  
|<span data-ttu-id="05b59-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="05b59-108">Event Source</span></span>|<span data-ttu-id="05b59-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="05b59-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="05b59-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="05b59-110">Component</span></span>|<span data-ttu-id="05b59-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="05b59-111">SQLEngine</span></span>|  
|<span data-ttu-id="05b59-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="05b59-112">Symbolic Name</span></span>|<span data-ttu-id="05b59-113">ALTERCOL_COLSET_DROP</span><span class="sxs-lookup"><span data-stu-id="05b59-113">ALTERCOL_COLSET_DROP</span></span>|  
|<span data-ttu-id="05b59-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="05b59-114">Message Text</span></span>|<span data-ttu-id="05b59-115">テーブル '%.\*ls' の列セット '%.\*ls' を削除できません。テーブルに 1025 以上の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="05b59-115">Cannot drop column set '%.\*ls' in table '%.\*ls' because the table contains more than 1025 columns.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="05b59-116">説明</span><span class="sxs-lookup"><span data-stu-id="05b59-116">Explanation</span></span>  
 <span data-ttu-id="05b59-117">テーブルには、スパース列または計算列として指定していない列を 1024 個まで含めることができます。</span><span class="sxs-lookup"><span data-stu-id="05b59-117">Tables can contain a maximum of 1024 columns that are not designated as sparse, or computed.</span></span> <span data-ttu-id="05b59-118">スパース列が原因でテーブルの列数が 1024 を超える場合は、テーブルに列セットを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b59-118">When sparse columns cause the table to exceed 1024 columns, a column set must be defined for the table.</span></span> <span data-ttu-id="05b59-119">参照先のテーブルには 1025 以上の列が含まれており、このテーブルから列セットを削除しようとしました。</span><span class="sxs-lookup"><span data-stu-id="05b59-119">The table referenced has more than 1024 columns and you have attempted to remove the column set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="05b59-120">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="05b59-120">User Action</span></span>  
 <span data-ttu-id="05b59-121">テーブルの現在の列では、列セットを保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="05b59-121">With the current columns in the table, you must retain the column set.</span></span>  
  
 <span data-ttu-id="05b59-122">列セットを削除するには、まずテーブルから列を削除し、列数が 1024 以下になるようにします。</span><span class="sxs-lookup"><span data-stu-id="05b59-122">To remove the column set, first remove columns from the table, until you have no more than 1024 columns.</span></span> <span data-ttu-id="05b59-123">その後、列セットを削除できます。</span><span class="sxs-lookup"><span data-stu-id="05b59-123">Then, you can remove the column set.</span></span>  
  
  
