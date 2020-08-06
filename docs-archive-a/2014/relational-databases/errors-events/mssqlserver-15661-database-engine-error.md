---
title: MSSQLSERVER_15661 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 966e23e8d970c36eba81253228cc18ed4af3ff77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631062"
---
# <a name="mssqlserver_15661"></a><span data-ttu-id="12338-102">MSSQLSERVER_15661</span><span class="sxs-lookup"><span data-stu-id="12338-102">MSSQLSERVER_15661</span></span>
    
## <a name="details"></a><span data-ttu-id="12338-103">詳細</span><span class="sxs-lookup"><span data-stu-id="12338-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="12338-104">製品名</span><span class="sxs-lookup"><span data-stu-id="12338-104">Product Name</span></span>|<span data-ttu-id="12338-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="12338-105">SQL Server</span></span>|  
|<span data-ttu-id="12338-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="12338-106">Event ID</span></span>|<span data-ttu-id="12338-107">15661</span><span class="sxs-lookup"><span data-stu-id="12338-107">15661</span></span>|  
|<span data-ttu-id="12338-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="12338-108">Event Source</span></span>|<span data-ttu-id="12338-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="12338-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="12338-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="12338-110">Component</span></span>|<span data-ttu-id="12338-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="12338-111">SQLEngine</span></span>|  
|<span data-ttu-id="12338-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="12338-112">Symbolic Name</span></span>|<span data-ttu-id="12338-113">SQLErrorNum15661</span><span class="sxs-lookup"><span data-stu-id="12338-113">SQLErrorNum15661</span></span>|  
|<span data-ttu-id="12338-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="12338-114">Message Text</span></span>|<span data-ttu-id="12338-115">sp_estimate_data_compression_savings ストアド プロシージャは、一時テーブルに対しては使用できません。</span><span class="sxs-lookup"><span data-stu-id="12338-115">The sp_estimate_data_compression_savings stored procedure cannot be used for temporary tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="12338-116">説明</span><span class="sxs-lookup"><span data-stu-id="12338-116">Explanation</span></span>  
 <span data-ttu-id="12338-117">一時テーブルが sp_estimate_data_compression_savings ストアド プロシージャの引数に使用されました。</span><span class="sxs-lookup"><span data-stu-id="12338-117">A temporary table was used as an argument for the sp_estimate_data_compression_savings stored procedure.</span></span> <span data-ttu-id="12338-118">一時テーブルの圧縮はサポートされていますが、sp_estimate_data_compression_savings を使用して圧縮保存を推定することはできません。</span><span class="sxs-lookup"><span data-stu-id="12338-118">Although the compression of temporary tables is supported, you cannot use sp_estimate_data_compression_savings to estimate the compression savings.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="12338-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="12338-119">User Action</span></span>  
 <span data-ttu-id="12338-120">sp_estimate_data_compression_savings の引数としての一時テーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="12338-120">Remove the temporary table as an argument for sp_estimate_data_compression_savings.</span></span>  
  
  
