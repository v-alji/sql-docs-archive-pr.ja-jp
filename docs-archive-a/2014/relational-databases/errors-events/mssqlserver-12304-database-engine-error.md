---
title: MSSQLSERVER_12304 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c2347fc46fe5ab83ef2ff46b81500cd737ed02d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642122"
---
# <a name="mssqlserver_12304"></a><span data-ttu-id="045c5-102">MSSQLSERVER_12304</span><span class="sxs-lookup"><span data-stu-id="045c5-102">MSSQLSERVER_12304</span></span>
    
## <a name="details"></a><span data-ttu-id="045c5-103">詳細</span><span class="sxs-lookup"><span data-stu-id="045c5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="045c5-104">製品名</span><span class="sxs-lookup"><span data-stu-id="045c5-104">Product Name</span></span>|<span data-ttu-id="045c5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="045c5-105">SQL Server</span></span>|  
|<span data-ttu-id="045c5-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="045c5-106">Event ID</span></span>|<span data-ttu-id="045c5-107">12304</span><span class="sxs-lookup"><span data-stu-id="045c5-107">12304</span></span>|  
|<span data-ttu-id="045c5-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="045c5-108">Event Source</span></span>|<span data-ttu-id="045c5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="045c5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="045c5-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="045c5-110">Component</span></span>|<span data-ttu-id="045c5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="045c5-111">SQLEngine</span></span>|  
|<span data-ttu-id="045c5-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="045c5-112">Symbolic Name</span></span>|<span data-ttu-id="045c5-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span><span class="sxs-lookup"><span data-stu-id="045c5-113">HK_UNSUPPORTED_IDENTITY_TABLE_VAR</span></span>|  
|<span data-ttu-id="045c5-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="045c5-114">Message Text</span></span>|<span data-ttu-id="045c5-115">ネイティブ コンパイル ストアド プロシージャのコンテキスト外にある型を使用する場合は、自らの任意の列と共に IDENTITY プロパティを使用するメモリ最適化テーブルを使用することはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="045c5-115">Using a memory optimized table type that uses the IDENTITY property with any of its columns is not supported when using the type outside the context of a natively compiled stored procedure.</span></span>|  
  
## <a name="user-action"></a><span data-ttu-id="045c5-116">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="045c5-116">User Action</span></span>  
 <span data-ttu-id="045c5-117">自らの任意の列と共に IDENTITY プロパティを使用するメモリ最適化テーブル型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="045c5-117">Do not use a memory-optimized table type that uses the identity property with any of its columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045c5-118">参照</span><span class="sxs-lookup"><span data-stu-id="045c5-118">See Also</span></span>  
 [<span data-ttu-id="045c5-119">インメモリ OLTP &#40;インメモリ最適化&#41;</span><span class="sxs-lookup"><span data-stu-id="045c5-119">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
