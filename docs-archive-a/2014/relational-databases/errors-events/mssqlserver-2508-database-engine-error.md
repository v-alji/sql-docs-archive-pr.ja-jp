---
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 11dd1c72c8cae868b7ebcb02e72ef0db81aeafe2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715314"
---
# <a name="mssqlserver_2508"></a><span data-ttu-id="6d7a6-102">MSSQLSERVER_2508</span><span class="sxs-lookup"><span data-stu-id="6d7a6-102">MSSQLSERVER_2508</span></span>
    
## <a name="details"></a><span data-ttu-id="6d7a6-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6d7a6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6d7a6-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6d7a6-104">Product Name</span></span>|<span data-ttu-id="6d7a6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6d7a6-105">SQL Server</span></span>|  
|<span data-ttu-id="6d7a6-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6d7a6-106">Event ID</span></span>|<span data-ttu-id="6d7a6-107">2508</span><span class="sxs-lookup"><span data-stu-id="6d7a6-107">2508</span></span>|  
|<span data-ttu-id="6d7a6-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6d7a6-108">Event Source</span></span>|<span data-ttu-id="6d7a6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6d7a6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6d7a6-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6d7a6-110">Component</span></span>|<span data-ttu-id="6d7a6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6d7a6-111">SQLEngine</span></span>|  
|<span data-ttu-id="6d7a6-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6d7a6-112">Symbolic Name</span></span>|<span data-ttu-id="6d7a6-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span><span class="sxs-lookup"><span data-stu-id="6d7a6-113">DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT</span></span>|  
|<span data-ttu-id="6d7a6-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6d7a6-114">Message Text</span></span>|<span data-ttu-id="6d7a6-115">オブジェクト "%.\*ls"、インデックス ID %d、パーティション ID %I64d、アロケーション ユニット ID %I64d (型 %.\*ls) の %.\*ls のカウントが正しくありません。</span><span class="sxs-lookup"><span data-stu-id="6d7a6-115">The %.\*ls count for object "%.\*ls", index ID %d, partition ID %I64d, alloc unit ID %I64d (type %.\*ls) is incorrect.</span></span> <span data-ttu-id="6d7a6-116">DBCC UPDATEUSAGE を実行してください。</span><span class="sxs-lookup"><span data-stu-id="6d7a6-116">Run DBCC UPDATEUSAGE.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6d7a6-117">説明</span><span class="sxs-lookup"><span data-stu-id="6d7a6-117">Explanation</span></span>  
 <span data-ttu-id="6d7a6-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以前のバージョンの [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] では、テーブルおよびインデックスの行やページのカウント値が正しくならないことがあります。</span><span class="sxs-lookup"><span data-stu-id="6d7a6-118">In versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] before [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], the values for the table and index row counts and page counts can become incorrect.</span></span> <span data-ttu-id="6d7a6-119">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] より前のバージョンで作成したデータベースはカウントが誤っている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d7a6-119">Databases that were created on versions prior to [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] may contain incorrect counts.</span></span> <span data-ttu-id="6d7a6-120">DBCC CHECKDB は、これらのエラーを検出するように拡張されており、エラーが見つかるとこの警告メッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="6d7a6-120">DBCC CHECKDB has been enhanced to detect these errors and returns this warning message when the error encountered.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6d7a6-121">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6d7a6-121">User Action</span></span>  
 <span data-ttu-id="6d7a6-122">指定したオブジェクトやインデックス、またはオブジェクトが格納されているデータベースに対して DBCC UPDATEUSAGE を実行し、無効なカウントを修正します。</span><span class="sxs-lookup"><span data-stu-id="6d7a6-122">Run DBCC UPDATEUSAGE against the specified object or index, or against the database in which the object is contained to correct the invalid counts.</span></span>  
  
  
