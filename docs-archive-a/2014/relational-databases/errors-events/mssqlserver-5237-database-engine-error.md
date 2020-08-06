---
title: MSSQLSERVER_5237 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 224317e290ce15aaed979129733b6273b3b663df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643849"
---
# <a name="mssqlserver_5237"></a><span data-ttu-id="05d27-102">MSSQLSERVER_5237</span><span class="sxs-lookup"><span data-stu-id="05d27-102">MSSQLSERVER_5237</span></span>
    
## <a name="details"></a><span data-ttu-id="05d27-103">詳細</span><span class="sxs-lookup"><span data-stu-id="05d27-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05d27-104">製品名</span><span class="sxs-lookup"><span data-stu-id="05d27-104">Product Name</span></span>|<span data-ttu-id="05d27-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="05d27-105">SQL Server</span></span>|  
|<span data-ttu-id="05d27-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="05d27-106">Event ID</span></span>|<span data-ttu-id="05d27-107">5237</span><span class="sxs-lookup"><span data-stu-id="05d27-107">5237</span></span>|  
|<span data-ttu-id="05d27-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="05d27-108">Event Source</span></span>|<span data-ttu-id="05d27-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="05d27-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="05d27-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="05d27-110">Component</span></span>|<span data-ttu-id="05d27-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="05d27-111">SQLEngine</span></span>|  
|<span data-ttu-id="05d27-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="05d27-112">Symbolic Name</span></span>|<span data-ttu-id="05d27-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span><span class="sxs-lookup"><span data-stu-id="05d27-113">DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE</span></span>|  
|<span data-ttu-id="05d27-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="05d27-114">Message Text</span></span>|<span data-ttu-id="05d27-115">オブジェクト 'NAME' (オブジェクト ID O_ID) で、内部クエリ エラーにより、DBCC クロス行セットのチェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="05d27-115">DBCC cross-rowset check failed for object 'NAME' (object ID O_ID) due to an internal query error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="05d27-116">説明</span><span class="sxs-lookup"><span data-stu-id="05d27-116">Explanation</span></span>  
 <span data-ttu-id="05d27-117">内部エラーが発生したため、DBCC は、クエリを実行してインデックス付きビューをチェックすることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="05d27-117">An internal error resulted in DBCC not being able to execute the query to check indexed views.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="05d27-118">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="05d27-118">User Action</span></span>  
 <span data-ttu-id="05d27-119">DBCC コマンドを再実行します。</span><span class="sxs-lookup"><span data-stu-id="05d27-119">Rerun the DBCC command.</span></span>  
  
  
