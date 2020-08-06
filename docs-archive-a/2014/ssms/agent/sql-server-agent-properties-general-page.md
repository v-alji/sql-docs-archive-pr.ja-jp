---
title: '[SQL Server エージェントのプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.agent.general.f1
ms.assetid: b51601e9-5454-43c6-bb5e-24eb2ff043c8
author: stevestein
ms.author: sstein
ms.openlocfilehash: a67d5431be4025c18b11d6791b016fa83e957810
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644270"
---
# <a name="sql-server-agent-properties-general-page"></a><span data-ttu-id="f10f6-102">[SQL Server エージェントのプロパティ] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="f10f6-102">SQL Server Agent Properties (General Page)</span></span>
  <span data-ttu-id="f10f6-103">このページを使用すると、エージェントサービスの全般プロパティを表示および変更 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] できます。</span><span class="sxs-lookup"><span data-stu-id="f10f6-103">Use this page to view and modify the general properties of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
## <a name="options"></a><span data-ttu-id="f10f6-104">Options</span><span class="sxs-lookup"><span data-stu-id="f10f6-104">Options</span></span>  
 <span data-ttu-id="f10f6-105">**サービスの状態**</span><span class="sxs-lookup"><span data-stu-id="f10f6-105">**Service state**</span></span>  
 <span data-ttu-id="f10f6-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスの現在の状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="f10f6-106">Displays the current state of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service.</span></span>  
  
 <span data-ttu-id="f10f6-107">**[予期しない停止時に SQL Server を自動的に再起動する]**</span><span class="sxs-lookup"><span data-stu-id="f10f6-107">**Auto restart SQL Server if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f10f6-108">エージェントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が予期せず停止した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動します。</span><span class="sxs-lookup"><span data-stu-id="f10f6-108">Agent restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stops unexpectedly.</span></span>  
  
 <span data-ttu-id="f10f6-109">**[予期しない停止時に SQL Server エージェントを自動的に再起動する]**</span><span class="sxs-lookup"><span data-stu-id="f10f6-109">**Auto restart SQL Server Agent if it stops unexpectedly**</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f10f6-110">は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントが予期せず停止した場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f10f6-110">restarts [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent if [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent stops unexpectedly.</span></span>  
  
 <span data-ttu-id="f10f6-111">**Filename**</span><span class="sxs-lookup"><span data-stu-id="f10f6-111">**Filename**</span></span>  
 <span data-ttu-id="f10f6-112">エラー ログのファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f10f6-112">Specify the file name for the error log.</span></span>  
  
 <span data-ttu-id="f10f6-113">**...**</span><span class="sxs-lookup"><span data-stu-id="f10f6-113">**...**</span></span>  
 <span data-ttu-id="f10f6-114">エラー ログ ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="f10f6-114">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="f10f6-115">**[実行トレース メッセージを含める]**</span><span class="sxs-lookup"><span data-stu-id="f10f6-115">**Include execution trace messages**</span></span>  
 <span data-ttu-id="f10f6-116">エラー ログに実行トレース メッセージを含めます。</span><span class="sxs-lookup"><span data-stu-id="f10f6-116">Includes execution trace messages in the error log.</span></span> <span data-ttu-id="f10f6-117">トレース メッセージにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの処理に関する詳細情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="f10f6-117">Trace messages provide detailed information on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent operation.</span></span> <span data-ttu-id="f10f6-118">そのため、このオプションを選択した場合は、ログ ファイルに必要なディスク領域が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="f10f6-118">Therefore, the log file requires more disk space when this option is selected.</span></span> <span data-ttu-id="f10f6-119">このオプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントに関係すると思われる問題をトラブルシューティングするときにのみ選択してください。</span><span class="sxs-lookup"><span data-stu-id="f10f6-119">This option should only be selected while troubleshooting a problem that may involve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.</span></span>  
  
 <span data-ttu-id="f10f6-120">**[OEM ファイルに書き込む]**</span><span class="sxs-lookup"><span data-stu-id="f10f6-120">**Write OEM file**</span></span>  
 <span data-ttu-id="f10f6-121">エラー ログ ファイルを非 Unicode ファイルとして書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f10f6-121">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="f10f6-122">これにより、ログ ファイルによって消費されるディスク領域が減少します。</span><span class="sxs-lookup"><span data-stu-id="f10f6-122">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="f10f6-123">ただし、このオプションを有効にすると Unicode データを含むメッセージが読み取りにくくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f10f6-123">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="f10f6-124">**[Net Send 受信者]**</span><span class="sxs-lookup"><span data-stu-id="f10f6-124">**Net send recipient**</span></span>  
 <span data-ttu-id="f10f6-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによってログ ファイルに書き込まれるメッセージの、Net Send 通知を受信するオペレーターの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="f10f6-125">Type the name of an operator to receive net send notification of messages that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f10f6-126">参照</span><span class="sxs-lookup"><span data-stu-id="f10f6-126">See Also</span></span>  
 <span data-ttu-id="f10f6-127">[通信](operators.md) </span><span class="sxs-lookup"><span data-stu-id="f10f6-127">[Operators](operators.md) </span></span>  
 [<span data-ttu-id="f10f6-128">SQL Server エージェント エラー ログ</span><span class="sxs-lookup"><span data-stu-id="f10f6-128">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
