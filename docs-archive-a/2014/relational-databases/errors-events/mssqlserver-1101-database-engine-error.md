---
title: MSSQLSERVER_1101 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 631b0ab1466815cbacfd71b4f9fd714fabd0f7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643930"
---
# <a name="mssqlserver_1101"></a><span data-ttu-id="8ef15-102">MSSQLSERVER_1101</span><span class="sxs-lookup"><span data-stu-id="8ef15-102">MSSQLSERVER_1101</span></span>
    
## <a name="details"></a><span data-ttu-id="8ef15-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8ef15-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8ef15-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8ef15-104">Product Name</span></span>|<span data-ttu-id="8ef15-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8ef15-105">SQL Server</span></span>|  
|<span data-ttu-id="8ef15-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8ef15-106">Event ID</span></span>|<span data-ttu-id="8ef15-107">1101</span><span class="sxs-lookup"><span data-stu-id="8ef15-107">1101</span></span>|  
|<span data-ttu-id="8ef15-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8ef15-108">Event Source</span></span>|<span data-ttu-id="8ef15-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8ef15-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8ef15-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8ef15-110">Component</span></span>|<span data-ttu-id="8ef15-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8ef15-111">SQLEngine</span></span>|  
|<span data-ttu-id="8ef15-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8ef15-112">Symbolic Name</span></span>|<span data-ttu-id="8ef15-113">NOALLOCPG</span><span class="sxs-lookup"><span data-stu-id="8ef15-113">NOALLOCPG</span></span>|  
|<span data-ttu-id="8ef15-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8ef15-114">Message Text</span></span>|<span data-ttu-id="8ef15-115">データベース '%.\*ls' の新しいページを割り当てられませんでした。ファイル グループ '%.\*ls' のディスク領域が不足しています。</span><span class="sxs-lookup"><span data-stu-id="8ef15-115">Could not allocate a new page for database '%.\*ls' because of insufficient disk space in filegroup '%.\*ls'.</span></span> <span data-ttu-id="8ef15-116">ファイル グループ内のオブジェクトの削除、ファイル グループへの新しいファイルの追加、またはファイル グループの既存のファイルの自動拡張の設定のいずれかを行って、必要な領域を作成してください。</span><span class="sxs-lookup"><span data-stu-id="8ef15-116">Create the necessary space by dropping objects in the filegroup, adding additional files to the filegroup, or setting autogrowth on for existing files in the filegroup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8ef15-117">説明</span><span class="sxs-lookup"><span data-stu-id="8ef15-117">Explanation</span></span>  
 <span data-ttu-id="8ef15-118">ファイル グループでディスク領域が不足しています。</span><span class="sxs-lookup"><span data-stu-id="8ef15-118">No disk space available in a filegroup.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8ef15-119">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8ef15-119">User Action</span></span>  
 <span data-ttu-id="8ef15-120">次の操作により、ファイル グループで領域を使用できるようになることがあります。</span><span class="sxs-lookup"><span data-stu-id="8ef15-120">The following actions may make space available in the filegroup.</span></span>  
  
-   <span data-ttu-id="8ef15-121">AUTOGROW をオンにする。</span><span class="sxs-lookup"><span data-stu-id="8ef15-121">Turn on AUTOGROW.</span></span>  
  
-   <span data-ttu-id="8ef15-122">ファイル グループにファイルをさらに追加する。</span><span class="sxs-lookup"><span data-stu-id="8ef15-122">Add more files to the file group.</span></span>  
  
-   <span data-ttu-id="8ef15-123">ファイル グループ内の不要なインデックスやテーブルを削除することにより、ディスク領域を解放する。</span><span class="sxs-lookup"><span data-stu-id="8ef15-123">Free up disk space by dropping unnecessary indexes or tables in the filegroup.</span></span>  
  
  
