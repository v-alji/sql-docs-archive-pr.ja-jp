---
title: MSSQLSERVER_3271 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3271 (Database Engine error)
ms.assetid: 21b8de4b-6624-4163-9561-1a6cc8fe3d51
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 56bdb5875dbba3fbe5037a308d713170a9b6f9ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640025"
---
# <a name="mssqlserver_3271"></a><span data-ttu-id="6f1c3-102">MSSQLSERVER_3271</span><span class="sxs-lookup"><span data-stu-id="6f1c3-102">MSSQLSERVER_3271</span></span>
    
## <a name="details"></a><span data-ttu-id="6f1c3-103">詳細</span><span class="sxs-lookup"><span data-stu-id="6f1c3-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6f1c3-104">製品名</span><span class="sxs-lookup"><span data-stu-id="6f1c3-104">Product Name</span></span>|<span data-ttu-id="6f1c3-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="6f1c3-105">SQL Server</span></span>|  
|<span data-ttu-id="6f1c3-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="6f1c3-106">Event ID</span></span>|<span data-ttu-id="6f1c3-107">3271</span><span class="sxs-lookup"><span data-stu-id="6f1c3-107">3271</span></span>|  
|<span data-ttu-id="6f1c3-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="6f1c3-108">Event Source</span></span>|<span data-ttu-id="6f1c3-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="6f1c3-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="6f1c3-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6f1c3-110">Component</span></span>|<span data-ttu-id="6f1c3-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="6f1c3-111">SQLEngine</span></span>|  
|<span data-ttu-id="6f1c3-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="6f1c3-112">Symbolic Name</span></span>|<span data-ttu-id="6f1c3-113">DMPIO_IO_ERROR</span><span class="sxs-lookup"><span data-stu-id="6f1c3-113">DMPIO_IO_ERROR</span></span>|  
|<span data-ttu-id="6f1c3-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6f1c3-114">Message Text</span></span>|<span data-ttu-id="6f1c3-115">ファイル "%ls:" %ls で回復できない I/O エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-115">A nonrecoverable I/O error occurred on file "%ls:" %ls.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6f1c3-116">説明</span><span class="sxs-lookup"><span data-stu-id="6f1c3-116">Explanation</span></span>  
 <span data-ttu-id="6f1c3-117">バックアップ操作または復元操作で I/O の実行中に、オペレーティング システムからエラーが通知された場合に生じる一般エラーです。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-117">This is a general error that occurs when the operating system raises an error while performing I/O during a backup or restore operation.</span></span> <span data-ttu-id="6f1c3-118">多くの場合、バックアップ メディアがいっぱいであることが原因です。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-118">In most situations the cause is simply that the backup medium is full.</span></span>  
  
 <span data-ttu-id="6f1c3-119">ディスクがいっぱいであることを示す、オペレーティング システムからのテキストがエラーに含まれている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-119">The error may include additional text from the operating system indicating that the disk is full.</span></span> <span data-ttu-id="6f1c3-120">サード パーティ製のバックアップ ソフトウェアによるバックアップ操作や復元操作の実行中は、バックアップが失敗したことを示すメッセージも表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-120">When performing a backup or restore operation with third-party backup software an additional message may occur indicating that the backup failed.</span></span> <span data-ttu-id="6f1c3-121">このメッセージは次のテキストのような内容になります。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-121">The message may look similar to the following text:</span></span>  
  
```  
"2005-08-02 16:05:16.04 spid55 Error: 18210, Severity: 16, State: 1.  
 2005-08-02 16:05:16.04 spid55 BackupVirtualDeviceFile  
::RequestDurableMedia: Flush failure on backup device 'VDINULL'.   
Operating system error 995(The I/O operation has been aborted because   
of either a thread exit or an application request.)."  
```  
  
 <span data-ttu-id="6f1c3-122">これは、バックアップ ソフトウェアにより、バックアップ操作または復元操作の中止が要求されたことを示しています。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-122">This is an indication that the backup software requested a termination of the backup or restore operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6f1c3-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6f1c3-123">User Action</span></span>  
 <span data-ttu-id="6f1c3-124">必要に応じて、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-124">Perform the following tasks as appropriate:</span></span>  
  
-   <span data-ttu-id="6f1c3-125">このエラーに先行して発生した、基になっているシステム エラー メッセージおよび SQL Server エラー メッセージで、障害の原因を調べます。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-125">Review the underlying system error messages and SQL Server error messages preceding this one to identify the cause of the failure.</span></span>  
  
-   <span data-ttu-id="6f1c3-126">バックアップ用および復元用のメディアに、十分な容量があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-126">Ensure that the backup and restore medium has sufficient space.</span></span>  
  
-   <span data-ttu-id="6f1c3-127">サード パーティ製のバックアップおよび復元ソフトウェアによってエラーが発生していれば、修正します。</span><span class="sxs-lookup"><span data-stu-id="6f1c3-127">Correct any errors raised by third-party backup and restore software.</span></span>  
  
  
