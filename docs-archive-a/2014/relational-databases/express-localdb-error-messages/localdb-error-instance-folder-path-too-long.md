---
title: LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: c178a308-8d99-47fc-8a49-5a480dc592f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 32ae8ebe102008d08a6059328ed57cd118ece019
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645093"
---
# <a name="localdb_error_instance_folder_path_too_long"></a><span data-ttu-id="a5f97-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span><span class="sxs-lookup"><span data-stu-id="a5f97-102">LOCALDB_ERROR_INSTANCE_FOLDER_PATH_TOO_LONG</span></span>
    
## <a name="details"></a><span data-ttu-id="a5f97-103">詳細</span><span class="sxs-lookup"><span data-stu-id="a5f97-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5f97-104">製品名</span><span class="sxs-lookup"><span data-stu-id="a5f97-104">Product Name</span></span>|<span data-ttu-id="a5f97-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5f97-105">SQL Server</span></span>|  
|<span data-ttu-id="a5f97-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a5f97-106">Event ID</span></span>|<span data-ttu-id="a5f97-107">260</span><span class="sxs-lookup"><span data-stu-id="a5f97-107">260</span></span>|  
|<span data-ttu-id="a5f97-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="a5f97-108">Event Source</span></span>|<span data-ttu-id="a5f97-109">SQL Server Local Database Runtime 12.0</span><span class="sxs-lookup"><span data-stu-id="a5f97-109">SQL Server Local Database Runtime 12.0</span></span>|  
|<span data-ttu-id="a5f97-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a5f97-110">Component</span></span>|<span data-ttu-id="a5f97-111">Local Database Runtime API</span><span class="sxs-lookup"><span data-stu-id="a5f97-111">Local Database Runtime API</span></span>|  
|<span data-ttu-id="a5f97-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="a5f97-112">Message Text</span></span>|<span data-ttu-id="a5f97-113">ローカル データベース インスタンス フォルダーの完全なパスの長さが MAX_PATH よりも長くなっています。</span><span class="sxs-lookup"><span data-stu-id="a5f97-113">The full path length of the Local Database instance folder is longer than MAX_PATH.</span></span> <span data-ttu-id="a5f97-114">インスタンスは、次のフォルダーに格納されている必要があります:%% LOCALAPPDATA%% \ Microsoft\Microsoft SQL Server ローカル Db\ インスタンス \\<インスタンス名 \> 。</span><span class="sxs-lookup"><span data-stu-id="a5f97-114">The instance must be stored in folder: %%LOCALAPPDATA%%\Microsoft\Microsoft SQL Server Local DB\Instances\\<instance name\>.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5f97-115">説明</span><span class="sxs-lookup"><span data-stu-id="a5f97-115">Explanation</span></span>  
 <span data-ttu-id="a5f97-116">インスタンスを格納するパスの長さが MAX_PATH を超過しています。</span><span class="sxs-lookup"><span data-stu-id="a5f97-116">The path where the instance should be stored is longer than MAX_PATH.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5f97-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="a5f97-117">User Action</span></span>  
 <span data-ttu-id="a5f97-118">MAX_PATH よりも短い新しいパスを作成してください。</span><span class="sxs-lookup"><span data-stu-id="a5f97-118">Create a new path that is shorter than MAX_PATH.</span></span>  
  
  
