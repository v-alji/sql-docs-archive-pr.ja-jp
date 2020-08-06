---
title: MSSQLSERVER_21862 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21862 (Database Engine error)
ms.assetid: a1d393dd-453b-4d45-9aa5-7d371213e32b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b945350d9c7a862d4274f464afbd7fc5472f732c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715334"
---
# <a name="mssqlserver_21862"></a><span data-ttu-id="278a4-102">MSSQLSERVER_21862</span><span class="sxs-lookup"><span data-stu-id="278a4-102">MSSQLSERVER_21862</span></span>
    
## <a name="details"></a><span data-ttu-id="278a4-103">詳細</span><span class="sxs-lookup"><span data-stu-id="278a4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="278a4-104">製品名</span><span class="sxs-lookup"><span data-stu-id="278a4-104">Product Name</span></span>|<span data-ttu-id="278a4-105">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="278a4-105">MSSQLSERVER</span></span>|  
|<span data-ttu-id="278a4-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="278a4-106">Event ID</span></span>|<span data-ttu-id="278a4-107">21862</span><span class="sxs-lookup"><span data-stu-id="278a4-107">21862</span></span>|  
|<span data-ttu-id="278a4-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="278a4-108">Event Source</span></span>|<span data-ttu-id="278a4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="278a4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="278a4-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="278a4-110">Component</span></span>|<span data-ttu-id="278a4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="278a4-111">SQLEngine</span></span>|  
|<span data-ttu-id="278a4-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="278a4-112">Symbolic Name</span></span>|<span data-ttu-id="278a4-113">SQLErrorNum21862</span><span class="sxs-lookup"><span data-stu-id="278a4-113">SQLErrorNum21862</span></span>|  
|<span data-ttu-id="278a4-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="278a4-114">Message Text</span></span>|<span data-ttu-id="278a4-115">FILESTREAM 列は、同期方法 'database snapshot' または 'database snapshot character' を使用して、パブリケーションでパブリッシュすることはできません。</span><span class="sxs-lookup"><span data-stu-id="278a4-115">FILESTREAM columns cannot be published in a publication by using a synchronization method of either 'database snapshot' or 'database snapshot character'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="278a4-116">説明</span><span class="sxs-lookup"><span data-stu-id="278a4-116">Explanation</span></span>  
 <span data-ttu-id="278a4-117">データベース スナップショットから FILESTREAM データにアクセスできないため、パブリケーションの同期方法に *database snapshot* パラメーターまたは *database_snapshot_character* パラメーターが指定されている場合、スナップショット エージェントは FILESTREAM データを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="278a4-117">Because FILESTREAM data cannot be accessed through a database snapshot, the snapshot agent will be unable to read FILESTREAM data when either the *database snapshot* or *database_snapshot_character* parameter is specified for the synchronization method of the publication.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="278a4-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="278a4-118">User Action</span></span>  
 <span data-ttu-id="278a4-119">パブリケーションの同期方法を *database snapshot* または *database_snapshot_character* 以外の方法に変更するか、パブリケーションから FILESTREAM 列を除外します。</span><span class="sxs-lookup"><span data-stu-id="278a4-119">Change the publication synchronization method to something other than *database snapshot* or *database_snapshot_character*, or just exclude the FILESTREAM column from the publication.</span></span>  
  
  
