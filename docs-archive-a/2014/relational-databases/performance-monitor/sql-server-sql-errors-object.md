---
title: SQL Server:SQL Errors オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 11bfb728e79b4fc175fb8a2fe16c9f1662a205ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713077"
---
# <a name="sql-server-sql-errors-object"></a><span data-ttu-id="4631b-102">SQL Server:SQL Errors オブジェクト</span><span class="sxs-lookup"><span data-stu-id="4631b-102">SQL Server, SQL Errors Object</span></span>
  <span data-ttu-id="4631b-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **SQLServer:SQL Errors** オブジェクトには、 **SQL Errors**を監視するカウンターが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4631b-103">The **SQLServer:SQL Errors** object in Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] provides counters to monitor **SQL Errors**.</span></span>  
  
 <span data-ttu-id="4631b-104">次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4631b-104">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **SQL Errors** counters.</span></span>  
  
|<span data-ttu-id="4631b-105">SQL Server SQL Errors のカウンター</span><span class="sxs-lookup"><span data-stu-id="4631b-105">SQL Server SQL Errors counters</span></span>|<span data-ttu-id="4631b-106">説明</span><span class="sxs-lookup"><span data-stu-id="4631b-106">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="4631b-107">**Errors/sec**</span><span class="sxs-lookup"><span data-stu-id="4631b-107">**Errors/sec**</span></span>|<span data-ttu-id="4631b-108">1 秒あたりのエラー数</span><span class="sxs-lookup"><span data-stu-id="4631b-108">Number of errors/sec.</span></span>|  
  
 <span data-ttu-id="4631b-109">オブジェクトの各カウンターには、次のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4631b-109">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="4631b-110">Item</span><span class="sxs-lookup"><span data-stu-id="4631b-110">Item</span></span>|<span data-ttu-id="4631b-111">定義</span><span class="sxs-lookup"><span data-stu-id="4631b-111">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="4631b-112">**_Total**</span><span class="sxs-lookup"><span data-stu-id="4631b-112">**_Total**</span></span>|<span data-ttu-id="4631b-113">すべてのエラーに関する情報。</span><span class="sxs-lookup"><span data-stu-id="4631b-113">Information for all errors.</span></span>|  
|<span data-ttu-id="4631b-114">**DB Offline Errors**</span><span class="sxs-lookup"><span data-stu-id="4631b-114">**DB Offline Errors**</span></span>|<span data-ttu-id="4631b-115">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で現在のデータベースがオフラインになる原因となる重大なエラーを追跡します。</span><span class="sxs-lookup"><span data-stu-id="4631b-115">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to take the current database offline.</span></span>|  
|<span data-ttu-id="4631b-116">**Info Errors**</span><span class="sxs-lookup"><span data-stu-id="4631b-116">**Info Errors**</span></span>|<span data-ttu-id="4631b-117">問題を起こしているわけではない、ユーザーに情報提供を行っているエラーメッセージの情報。</span><span class="sxs-lookup"><span data-stu-id="4631b-117">Information related to error messages that provide information to users but do not cause errors.</span></span>|  
|<span data-ttu-id="4631b-118">**Kill Connection Errors**</span><span class="sxs-lookup"><span data-stu-id="4631b-118">**Kill Connection Errors**</span></span>|<span data-ttu-id="4631b-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在の接続を強制的に切断する原因となる重大なエラーを追跡します。</span><span class="sxs-lookup"><span data-stu-id="4631b-119">Tracks severe errors that cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to kill the current connection.</span></span>|  
|<span data-ttu-id="4631b-120">**User Errors**</span><span class="sxs-lookup"><span data-stu-id="4631b-120">**User Errors**</span></span>|<span data-ttu-id="4631b-121">ユーザー エラーに関する情報。</span><span class="sxs-lookup"><span data-stu-id="4631b-121">Information about user errors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4631b-122">参照</span><span class="sxs-lookup"><span data-stu-id="4631b-122">See Also</span></span>  
 [<span data-ttu-id="4631b-123">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="4631b-123">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
