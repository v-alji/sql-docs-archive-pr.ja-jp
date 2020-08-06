---
title: '[データベースのプロパティ] ([変更の追跡] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.changetracking.f1
ms.assetid: 9b929640-bc62-449b-9b06-b5a77b8cf372
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4107f81ef4cdf19df60d4a70d8e79007f2c9270c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718242"
---
# <a name="database-properties-changetracking-page"></a><span data-ttu-id="b8e2b-102">[データベースのプロパティ] ([変更の追跡] ページ)</span><span class="sxs-lookup"><span data-stu-id="b8e2b-102">Database Properties (ChangeTracking Page)</span></span>
  <span data-ttu-id="b8e2b-103">このページを使用すると、選択されているデータベースの変更の追跡設定を表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-103">Use this page to view or modify change tracking settings for the selected database.</span></span> <span data-ttu-id="b8e2b-104">このページで使用可能なオプションの詳細については、「[変更の追跡の有効化と無効化 &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-104">For more information about the options available on this page, see [Enable and Disable Change Tracking &#40;SQL Server&#41;](../track-changes/enable-and-disable-change-tracking-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="b8e2b-105">Options</span><span class="sxs-lookup"><span data-stu-id="b8e2b-105">Options</span></span>  
 <span data-ttu-id="b8e2b-106">**変更の追跡**</span><span class="sxs-lookup"><span data-stu-id="b8e2b-106">**Change Tracking**</span></span>  
 <span data-ttu-id="b8e2b-107">データベースの変更の追跡の有効/無効を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-107">Use to enable or disable change tracking for the database.</span></span>  
  
 <span data-ttu-id="b8e2b-108">変更の追跡を有効にするには、データベースを変更する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-108">To enable change tracking, you must have permission to modify the database.</span></span>  
  
 <span data-ttu-id="b8e2b-109">この値を **True** に設定すると、個々のテーブルで変更の追跡を有効にできるデータベース オプションが設定されます。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-109">Setting the value to **True** sets a database option that allows change tracking to be enabled on individual tables.</span></span>  
  
 <span data-ttu-id="b8e2b-110">[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql)を使用して変更追跡を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-110">You can also configure change tracking by using [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="b8e2b-111">**保有期間**</span><span class="sxs-lookup"><span data-stu-id="b8e2b-111">**Retention Period**</span></span>  
 <span data-ttu-id="b8e2b-112">データベースに変更追跡情報を保持する最低限の期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-112">Specifies the minimum period for keeping change track information in the database.</span></span> <span data-ttu-id="b8e2b-113">データは、 **[自動クリーンアップ]** の値が **True**の場合にのみ削除されます。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-113">Data is removed only if the **Auto Clean-Up**value is **True**.</span></span>  
  
 <span data-ttu-id="b8e2b-114">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-114">The default value is 2.</span></span>  
  
 <span data-ttu-id="b8e2b-115">**[保有期間の単位]**</span><span class="sxs-lookup"><span data-stu-id="b8e2b-115">**Retention Period Units**</span></span>  
 <span data-ttu-id="b8e2b-116">保有期間の値の単位を指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-116">Specifies the units for the Retention Period value.</span></span> <span data-ttu-id="b8e2b-117">**[日]** 、 **[時間]** 、または **[分]** を選択できます。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-117">You can select **Days**, **Hours**, or **Minutes**.</span></span> <span data-ttu-id="b8e2b-118">既定値は **[日]** です。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-118">The default value is **Days**.</span></span>  
  
 <span data-ttu-id="b8e2b-119">最小保有期間は 1 分です。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-119">The minimum retention period is 1 minute.</span></span> <span data-ttu-id="b8e2b-120">最大保有期間はありません。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-120">There is no maximum retention period.</span></span>  
  
 <span data-ttu-id="b8e2b-121">**[自動クリーンアップ]**</span><span class="sxs-lookup"><span data-stu-id="b8e2b-121">**Auto Clean-Up**</span></span>  
 <span data-ttu-id="b8e2b-122">指定した保有期間を過ぎると変更追跡情報が自動的に削除されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-122">Indicates whether change tracking information is automatically removed after the specified retention period.</span></span>  
  
 <span data-ttu-id="b8e2b-123">**[自動クリーンアップ]** を有効にすると、以前のカスタム保有期間はすべて既定の保有期間 (2 日) にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="b8e2b-123">Enabling **Auto Clean-Up** resets any previous custom retention period to the default retention period of 2 days.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e2b-124">参照</span><span class="sxs-lookup"><span data-stu-id="b8e2b-124">See Also</span></span>  
 <span data-ttu-id="b8e2b-125">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b8e2b-125">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 [<span data-ttu-id="b8e2b-126">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="b8e2b-126">CREATE DATABASE &#40;SQL Server Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-database-sql-server-transact-sql)  
  
  
