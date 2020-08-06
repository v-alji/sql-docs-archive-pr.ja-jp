---
title: '[SQL Server エージェント エラー ログの構成] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.errorlog.configure.f1
ms.assetid: e08de622-6f87-470c-aee0-b2d6cb6cca88
author: stevestein
ms.author: sstein
ms.openlocfilehash: bd4c083ea7e7d220d5da20594079b7679c0bb724
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642506"
---
# <a name="configure-sql-server-agent-error-logs-general-page"></a><span data-ttu-id="16415-102">[SQL Server エージェント エラー ログの構成] \([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="16415-102">Configure SQL Server Agent Error Logs (General Page)</span></span>
  <span data-ttu-id="16415-103">この画面を使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのエラー ログ設定の表示と更新を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="16415-103">Use this screen to view and update settings for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent error logging.</span></span>  
  
## <a name="options"></a><span data-ttu-id="16415-104">Options</span><span class="sxs-lookup"><span data-stu-id="16415-104">Options</span></span>  
 <span data-ttu-id="16415-105">**[エラー ログ ファイル]**</span><span class="sxs-lookup"><span data-stu-id="16415-105">**Error log file**</span></span>  
 <span data-ttu-id="16415-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントがエラー ログを書き込むファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="16415-106">Specifies the file to which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent writes error logs.</span></span>  
  
 <span data-ttu-id="16415-107">**...**</span><span class="sxs-lookup"><span data-stu-id="16415-107">**...**</span></span>  
 <span data-ttu-id="16415-108">エラー ログ ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="16415-108">Browse to the error log file.</span></span>  
  
 <span data-ttu-id="16415-109">**[OEM エラー ログを書き込む]**</span><span class="sxs-lookup"><span data-stu-id="16415-109">**Write OEM error log**</span></span>  
 <span data-ttu-id="16415-110">エラー ログ ファイルを非 Unicode ファイルとして書き込みます。</span><span class="sxs-lookup"><span data-stu-id="16415-110">Writes the error log file as a non-Unicode file.</span></span> <span data-ttu-id="16415-111">これにより、ログ ファイルによって消費されるディスク領域が減少します。</span><span class="sxs-lookup"><span data-stu-id="16415-111">This reduces the amount of disk space consumed by the log file.</span></span> <span data-ttu-id="16415-112">ただし、このオプションを有効にすると Unicode データを含むメッセージが読み取りにくくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="16415-112">However, messages that include Unicode data may be more difficult to read when this option is enabled.</span></span>  
  
 <span data-ttu-id="16415-113">**エラー**</span><span class="sxs-lookup"><span data-stu-id="16415-113">**Errors**</span></span>  
 <span data-ttu-id="16415-114">ログ ファイルにエラーおよび情報メッセージのみを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="16415-114">Writes only errors and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="16415-115">**Warnings**</span><span class="sxs-lookup"><span data-stu-id="16415-115">**Warnings**</span></span>  
 <span data-ttu-id="16415-116">ログ ファイルに警告および情報メッセージのみを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="16415-116">Writes only warnings and informational messages to the log file.</span></span>  
  
 <span data-ttu-id="16415-117">**情報**</span><span class="sxs-lookup"><span data-stu-id="16415-117">**Information**</span></span>  
 <span data-ttu-id="16415-118">ログ ファイルに情報メッセージのみを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="16415-118">Writes only informational messages to the log file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16415-119">参照</span><span class="sxs-lookup"><span data-stu-id="16415-119">See Also</span></span>  
 [<span data-ttu-id="16415-120">SQL Server エージェント エラー ログ</span><span class="sxs-lookup"><span data-stu-id="16415-120">SQL Server Agent Error Log</span></span>](sql-server-agent-error-log.md)  
  
  
