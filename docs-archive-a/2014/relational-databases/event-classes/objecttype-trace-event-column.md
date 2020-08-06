---
title: ObjectType トレース イベント列 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- SQL Server event classes, Object Type column values
- events [SQL Server], Object Type column values
- event classes [SQL Server], Object Type column values
- Object Type column values [SQL Server]
ms.assetid: 42f85c50-34c9-49ca-955f-af9595e2707f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1f90661e5ebedc91505989c3d80dcec78436ce86
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633863"
---
# <a name="objecttype-trace-event-column"></a><span data-ttu-id="a1912-102">ObjectType トレース イベント列</span><span class="sxs-lookup"><span data-stu-id="a1912-102">ObjectType Trace Event Column</span></span>
  <span data-ttu-id="a1912-103">Object Type トレース イベント列は、さまざまなトレース イベントで使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1912-103">The Object Type trace event column is used in a variety of trace events.</span></span> <span data-ttu-id="a1912-104">このトピックでは、この列の値と、その値に関連付けられている定義について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1912-104">This topic describes the possible values of this column and their associated definitions.</span></span>  
  
## <a name="object-type-column-values"></a><span data-ttu-id="a1912-105">ObjectType 列の値</span><span class="sxs-lookup"><span data-stu-id="a1912-105">Object Type Column Values</span></span>  
  
|<span data-ttu-id="a1912-106">値</span><span class="sxs-lookup"><span data-stu-id="a1912-106">Value</span></span>|<span data-ttu-id="a1912-107">定義</span><span class="sxs-lookup"><span data-stu-id="a1912-107">Definition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="a1912-108">8259</span><span class="sxs-lookup"><span data-stu-id="a1912-108">8259</span></span>|<span data-ttu-id="a1912-109">CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="a1912-109">Check Constraint</span></span>|  
|<span data-ttu-id="a1912-110">8260</span><span class="sxs-lookup"><span data-stu-id="a1912-110">8260</span></span>|<span data-ttu-id="a1912-111">既定値 (制約またはスタンドアロン)</span><span class="sxs-lookup"><span data-stu-id="a1912-111">Default (constraint or standalone)</span></span>|  
|<span data-ttu-id="a1912-112">8262</span><span class="sxs-lookup"><span data-stu-id="a1912-112">8262</span></span>|<span data-ttu-id="a1912-113">外部キー制約</span><span class="sxs-lookup"><span data-stu-id="a1912-113">Foreign-key Constraint</span></span>|  
|<span data-ttu-id="a1912-114">8272</span><span class="sxs-lookup"><span data-stu-id="a1912-114">8272</span></span>|<span data-ttu-id="a1912-115">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a1912-115">Stored Procedure</span></span>|  
|<span data-ttu-id="a1912-116">8274</span><span class="sxs-lookup"><span data-stu-id="a1912-116">8274</span></span>|<span data-ttu-id="a1912-117">ルール</span><span class="sxs-lookup"><span data-stu-id="a1912-117">Rule</span></span>|  
|<span data-ttu-id="a1912-118">8275</span><span class="sxs-lookup"><span data-stu-id="a1912-118">8275</span></span>|<span data-ttu-id="a1912-119">システム テーブル</span><span class="sxs-lookup"><span data-stu-id="a1912-119">System Table</span></span>|  
|<span data-ttu-id="a1912-120">8276</span><span class="sxs-lookup"><span data-stu-id="a1912-120">8276</span></span>|<span data-ttu-id="a1912-121">サーバーのトリガー</span><span class="sxs-lookup"><span data-stu-id="a1912-121">Trigger on Server</span></span>|  
|<span data-ttu-id="a1912-122">8277</span><span class="sxs-lookup"><span data-stu-id="a1912-122">8277</span></span>|<span data-ttu-id="a1912-123">(ユーザー定義) テーブル</span><span class="sxs-lookup"><span data-stu-id="a1912-123">(User-defined) Table</span></span>|  
|<span data-ttu-id="a1912-124">8278</span><span class="sxs-lookup"><span data-stu-id="a1912-124">8278</span></span>|<span data-ttu-id="a1912-125">表示</span><span class="sxs-lookup"><span data-stu-id="a1912-125">View</span></span>|  
|<span data-ttu-id="a1912-126">8280</span><span class="sxs-lookup"><span data-stu-id="a1912-126">8280</span></span>|<span data-ttu-id="a1912-127">拡張ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a1912-127">Extended Stored Procedure</span></span>|  
|<span data-ttu-id="a1912-128">16724</span><span class="sxs-lookup"><span data-stu-id="a1912-128">16724</span></span>|<span data-ttu-id="a1912-129">CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="a1912-129">CLR Trigger</span></span>|  
|<span data-ttu-id="a1912-130">16964</span><span class="sxs-lookup"><span data-stu-id="a1912-130">16964</span></span>|<span data-ttu-id="a1912-131">データベース</span><span class="sxs-lookup"><span data-stu-id="a1912-131">Database</span></span>|  
|<span data-ttu-id="a1912-132">16975</span><span class="sxs-lookup"><span data-stu-id="a1912-132">16975</span></span>|<span data-ttu-id="a1912-133">Object</span><span class="sxs-lookup"><span data-stu-id="a1912-133">Object</span></span>|  
|<span data-ttu-id="a1912-134">17222</span><span class="sxs-lookup"><span data-stu-id="a1912-134">17222</span></span>|<span data-ttu-id="a1912-135">フルテキスト カタログ</span><span class="sxs-lookup"><span data-stu-id="a1912-135">FullText Catalog</span></span>|  
|<span data-ttu-id="a1912-136">17232</span><span class="sxs-lookup"><span data-stu-id="a1912-136">17232</span></span>|<span data-ttu-id="a1912-137">CLR ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a1912-137">CLR Stored Procedure</span></span>|  
|<span data-ttu-id="a1912-138">17235</span><span class="sxs-lookup"><span data-stu-id="a1912-138">17235</span></span>|<span data-ttu-id="a1912-139">スキーマ</span><span class="sxs-lookup"><span data-stu-id="a1912-139">Schema</span></span>|  
|<span data-ttu-id="a1912-140">17475</span><span class="sxs-lookup"><span data-stu-id="a1912-140">17475</span></span>|<span data-ttu-id="a1912-141">資格情報</span><span class="sxs-lookup"><span data-stu-id="a1912-141">Credential</span></span>|  
|<span data-ttu-id="a1912-142">17491</span><span class="sxs-lookup"><span data-stu-id="a1912-142">17491</span></span>|<span data-ttu-id="a1912-143">DDL イベント</span><span class="sxs-lookup"><span data-stu-id="a1912-143">DDL Event</span></span>|  
|<span data-ttu-id="a1912-144">17741</span><span class="sxs-lookup"><span data-stu-id="a1912-144">17741</span></span>|<span data-ttu-id="a1912-145">管理イベント</span><span class="sxs-lookup"><span data-stu-id="a1912-145">Management Event</span></span>|  
|<span data-ttu-id="a1912-146">17747</span><span class="sxs-lookup"><span data-stu-id="a1912-146">17747</span></span>|<span data-ttu-id="a1912-147">セキュリティ イベント</span><span class="sxs-lookup"><span data-stu-id="a1912-147">Security Event</span></span>|  
|<span data-ttu-id="a1912-148">17749</span><span class="sxs-lookup"><span data-stu-id="a1912-148">17749</span></span>|<span data-ttu-id="a1912-149">ユーザー イベント</span><span class="sxs-lookup"><span data-stu-id="a1912-149">User Event</span></span>|  
|<span data-ttu-id="a1912-150">17985</span><span class="sxs-lookup"><span data-stu-id="a1912-150">17985</span></span>|<span data-ttu-id="a1912-151">CLR 集合関数</span><span class="sxs-lookup"><span data-stu-id="a1912-151">CLR Aggregate Function</span></span>|  
|<span data-ttu-id="a1912-152">17993</span><span class="sxs-lookup"><span data-stu-id="a1912-152">17993</span></span>|<span data-ttu-id="a1912-153">インライン テーブル値 SQL 関数</span><span class="sxs-lookup"><span data-stu-id="a1912-153">Inline Table-valued SQL Function</span></span>|  
|<span data-ttu-id="a1912-154">18000</span><span class="sxs-lookup"><span data-stu-id="a1912-154">18000</span></span>|<span data-ttu-id="a1912-155">パーティション関数</span><span class="sxs-lookup"><span data-stu-id="a1912-155">Partition Function</span></span>|  
|<span data-ttu-id="a1912-156">18002</span><span class="sxs-lookup"><span data-stu-id="a1912-156">18002</span></span>|<span data-ttu-id="a1912-157">レプリケーション フィルター プロシージャ</span><span class="sxs-lookup"><span data-stu-id="a1912-157">Replication Filter Procedure</span></span>|  
|<span data-ttu-id="a1912-158">18004</span><span class="sxs-lookup"><span data-stu-id="a1912-158">18004</span></span>|<span data-ttu-id="a1912-159">テーブル値 SQL 関数</span><span class="sxs-lookup"><span data-stu-id="a1912-159">Table-valued SQL Function</span></span>|  
|<span data-ttu-id="a1912-160">18259</span><span class="sxs-lookup"><span data-stu-id="a1912-160">18259</span></span>|<span data-ttu-id="a1912-161">サーバー ロール</span><span class="sxs-lookup"><span data-stu-id="a1912-161">Server Role</span></span>|  
|<span data-ttu-id="a1912-162">18263</span><span class="sxs-lookup"><span data-stu-id="a1912-162">18263</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="a1912-163">Windows グループ</span><span class="sxs-lookup"><span data-stu-id="a1912-163">Windows Group</span></span>|  
|<span data-ttu-id="a1912-164">19265</span><span class="sxs-lookup"><span data-stu-id="a1912-164">19265</span></span>|<span data-ttu-id="a1912-165">非対称キー</span><span class="sxs-lookup"><span data-stu-id="a1912-165">Asymmetric Key</span></span>|  
|<span data-ttu-id="a1912-166">19277</span><span class="sxs-lookup"><span data-stu-id="a1912-166">19277</span></span>|<span data-ttu-id="a1912-167">マスター キー</span><span class="sxs-lookup"><span data-stu-id="a1912-167">Master Key</span></span>|  
|<span data-ttu-id="a1912-168">19280</span><span class="sxs-lookup"><span data-stu-id="a1912-168">19280</span></span>|<span data-ttu-id="a1912-169">主キー</span><span class="sxs-lookup"><span data-stu-id="a1912-169">Primary Key</span></span>|  
|<span data-ttu-id="a1912-170">19283</span><span class="sxs-lookup"><span data-stu-id="a1912-170">19283</span></span>|<span data-ttu-id="a1912-171">ObfusKey</span><span class="sxs-lookup"><span data-stu-id="a1912-171">ObfusKey</span></span>|  
|<span data-ttu-id="a1912-172">19521</span><span class="sxs-lookup"><span data-stu-id="a1912-172">19521</span></span>|<span data-ttu-id="a1912-173">非対称キー ログイン</span><span class="sxs-lookup"><span data-stu-id="a1912-173">Asymmetric Key Login</span></span>|  
|<span data-ttu-id="a1912-174">19523</span><span class="sxs-lookup"><span data-stu-id="a1912-174">19523</span></span>|<span data-ttu-id="a1912-175">証明書ログイン</span><span class="sxs-lookup"><span data-stu-id="a1912-175">Certificate Login</span></span>|  
|<span data-ttu-id="a1912-176">19538</span><span class="sxs-lookup"><span data-stu-id="a1912-176">19538</span></span>|<span data-ttu-id="a1912-177">Role</span><span class="sxs-lookup"><span data-stu-id="a1912-177">Role</span></span>|  
|<span data-ttu-id="a1912-178">19539</span><span class="sxs-lookup"><span data-stu-id="a1912-178">19539</span></span>|<span data-ttu-id="a1912-179">SQL ログイン</span><span class="sxs-lookup"><span data-stu-id="a1912-179">SQL Login</span></span>|  
|<span data-ttu-id="a1912-180">19543</span><span class="sxs-lookup"><span data-stu-id="a1912-180">19543</span></span>|<span data-ttu-id="a1912-181">Windows ログイン</span><span class="sxs-lookup"><span data-stu-id="a1912-181">Windows Login</span></span>|  
|<span data-ttu-id="a1912-182">20034</span><span class="sxs-lookup"><span data-stu-id="a1912-182">20034</span></span>|<span data-ttu-id="a1912-183">リモート サービス バインド</span><span class="sxs-lookup"><span data-stu-id="a1912-183">Remote Service Binding</span></span>|  
|<span data-ttu-id="a1912-184">20036</span><span class="sxs-lookup"><span data-stu-id="a1912-184">20036</span></span>|<span data-ttu-id="a1912-185">データベースに関するイベント通知</span><span class="sxs-lookup"><span data-stu-id="a1912-185">Event Notification on Database</span></span>|  
|<span data-ttu-id="a1912-186">20037</span><span class="sxs-lookup"><span data-stu-id="a1912-186">20037</span></span>|<span data-ttu-id="a1912-187">イベント通知</span><span class="sxs-lookup"><span data-stu-id="a1912-187">Event Notification</span></span>|  
|<span data-ttu-id="a1912-188">20038</span><span class="sxs-lookup"><span data-stu-id="a1912-188">20038</span></span>|<span data-ttu-id="a1912-189">SQL スカラー関数</span><span class="sxs-lookup"><span data-stu-id="a1912-189">Scalar SQL Function</span></span>|  
|<span data-ttu-id="a1912-190">20047</span><span class="sxs-lookup"><span data-stu-id="a1912-190">20047</span></span>|<span data-ttu-id="a1912-191">オブジェクトに関するイベント通知</span><span class="sxs-lookup"><span data-stu-id="a1912-191">Event Notification on Object</span></span>|  
|<span data-ttu-id="a1912-192">20051</span><span class="sxs-lookup"><span data-stu-id="a1912-192">20051</span></span>|<span data-ttu-id="a1912-193">シノニム</span><span class="sxs-lookup"><span data-stu-id="a1912-193">Synonym</span></span>|  
|<span data-ttu-id="a1912-194">20307</span><span class="sxs-lookup"><span data-stu-id="a1912-194">20307</span></span>|<span data-ttu-id="a1912-195">Sequence</span><span class="sxs-lookup"><span data-stu-id="a1912-195">Sequence</span></span>|  
|<span data-ttu-id="a1912-196">20549</span><span class="sxs-lookup"><span data-stu-id="a1912-196">20549</span></span>|<span data-ttu-id="a1912-197">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="a1912-197">End Point</span></span>|  
|<span data-ttu-id="a1912-198">20801</span><span class="sxs-lookup"><span data-stu-id="a1912-198">20801</span></span>|<span data-ttu-id="a1912-199">キャッシュされる可能性のあるアドホック クエリ</span><span class="sxs-lookup"><span data-stu-id="a1912-199">Adhoc Queries which may be cached</span></span>|  
|<span data-ttu-id="a1912-200">20816</span><span class="sxs-lookup"><span data-stu-id="a1912-200">20816</span></span>|<span data-ttu-id="a1912-201">キャッシュされる可能性のある準備されたクエリ</span><span class="sxs-lookup"><span data-stu-id="a1912-201">Prepared Queries which may be cached</span></span>|  
|<span data-ttu-id="a1912-202">20819</span><span class="sxs-lookup"><span data-stu-id="a1912-202">20819</span></span>|<span data-ttu-id="a1912-203">Service Broker サービス キュー</span><span class="sxs-lookup"><span data-stu-id="a1912-203">Service Broker Service Queue</span></span>|  
|<span data-ttu-id="a1912-204">20821</span><span class="sxs-lookup"><span data-stu-id="a1912-204">20821</span></span>|<span data-ttu-id="a1912-205">UNIQUE 制約</span><span class="sxs-lookup"><span data-stu-id="a1912-205">Unique Constraint</span></span>|  
|<span data-ttu-id="a1912-206">21057</span><span class="sxs-lookup"><span data-stu-id="a1912-206">21057</span></span>|<span data-ttu-id="a1912-207">アプリケーション ロール</span><span class="sxs-lookup"><span data-stu-id="a1912-207">Application Role</span></span>|  
|<span data-ttu-id="a1912-208">21059</span><span class="sxs-lookup"><span data-stu-id="a1912-208">21059</span></span>|<span data-ttu-id="a1912-209">Certificate</span><span class="sxs-lookup"><span data-stu-id="a1912-209">Certificate</span></span>|  
|<span data-ttu-id="a1912-210">21075</span><span class="sxs-lookup"><span data-stu-id="a1912-210">21075</span></span>|<span data-ttu-id="a1912-211">サーバー</span><span class="sxs-lookup"><span data-stu-id="a1912-211">Server</span></span>|  
|<span data-ttu-id="a1912-212">21076</span><span class="sxs-lookup"><span data-stu-id="a1912-212">21076</span></span>|<span data-ttu-id="a1912-213">Transact-SQL トリガー</span><span class="sxs-lookup"><span data-stu-id="a1912-213">Transact-SQL Trigger</span></span>|  
|<span data-ttu-id="a1912-214">21313</span><span class="sxs-lookup"><span data-stu-id="a1912-214">21313</span></span>|<span data-ttu-id="a1912-215">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="a1912-215">Assembly</span></span>|  
|<span data-ttu-id="a1912-216">21318</span><span class="sxs-lookup"><span data-stu-id="a1912-216">21318</span></span>|<span data-ttu-id="a1912-217">CLR スカラー関数</span><span class="sxs-lookup"><span data-stu-id="a1912-217">CLR Scalar Function</span></span>|  
|<span data-ttu-id="a1912-218">21321</span><span class="sxs-lookup"><span data-stu-id="a1912-218">21321</span></span>|<span data-ttu-id="a1912-219">インライン スカラー SQL 関数</span><span class="sxs-lookup"><span data-stu-id="a1912-219">Inline scalar SQL Function</span></span>|  
|<span data-ttu-id="a1912-220">21328</span><span class="sxs-lookup"><span data-stu-id="a1912-220">21328</span></span>|<span data-ttu-id="a1912-221">パーティション構成</span><span class="sxs-lookup"><span data-stu-id="a1912-221">Partition Scheme</span></span>|  
|<span data-ttu-id="a1912-222">21333</span><span class="sxs-lookup"><span data-stu-id="a1912-222">21333</span></span>|<span data-ttu-id="a1912-223">User</span><span class="sxs-lookup"><span data-stu-id="a1912-223">User</span></span>|  
|<span data-ttu-id="a1912-224">21571</span><span class="sxs-lookup"><span data-stu-id="a1912-224">21571</span></span>|<span data-ttu-id="a1912-225">Service Broker サービス コントラクト</span><span class="sxs-lookup"><span data-stu-id="a1912-225">Service Broker Service Contract</span></span>|  
|<span data-ttu-id="a1912-226">21572</span><span class="sxs-lookup"><span data-stu-id="a1912-226">21572</span></span>|<span data-ttu-id="a1912-227">データベースのトリガー</span><span class="sxs-lookup"><span data-stu-id="a1912-227">Trigger on Database</span></span>|  
|<span data-ttu-id="a1912-228">21574</span><span class="sxs-lookup"><span data-stu-id="a1912-228">21574</span></span>|<span data-ttu-id="a1912-229">CLR テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="a1912-229">CLR Table-valued Function</span></span>|  
|<span data-ttu-id="a1912-230">21577</span><span class="sxs-lookup"><span data-stu-id="a1912-230">21577</span></span>|<span data-ttu-id="a1912-231">内部テーブル (XML ノード テーブル、キュー テーブルなど)</span><span class="sxs-lookup"><span data-stu-id="a1912-231">Internal Table (For example, XML Node Table, Queue Table.)</span></span>|  
|<span data-ttu-id="a1912-232">21581</span><span class="sxs-lookup"><span data-stu-id="a1912-232">21581</span></span>|<span data-ttu-id="a1912-233">Service Broker メッセージ型</span><span class="sxs-lookup"><span data-stu-id="a1912-233">Service Broker Message Type</span></span>|  
|<span data-ttu-id="a1912-234">21586</span><span class="sxs-lookup"><span data-stu-id="a1912-234">21586</span></span>|<span data-ttu-id="a1912-235">Service Broker ルート</span><span class="sxs-lookup"><span data-stu-id="a1912-235">Service Broker Route</span></span>|  
|<span data-ttu-id="a1912-236">21587</span><span class="sxs-lookup"><span data-stu-id="a1912-236">21587</span></span>|<span data-ttu-id="a1912-237">統計</span><span class="sxs-lookup"><span data-stu-id="a1912-237">Statistics</span></span>|  
|<span data-ttu-id="a1912-238">21825</span><span class="sxs-lookup"><span data-stu-id="a1912-238">21825</span></span><br /><br /> <span data-ttu-id="a1912-239">21827</span><span class="sxs-lookup"><span data-stu-id="a1912-239">21827</span></span><br /><br /> <span data-ttu-id="a1912-240">21831</span><span class="sxs-lookup"><span data-stu-id="a1912-240">21831</span></span><br /><br /> <span data-ttu-id="a1912-241">21843</span><span class="sxs-lookup"><span data-stu-id="a1912-241">21843</span></span><br /><br /> <span data-ttu-id="a1912-242">21847</span><span class="sxs-lookup"><span data-stu-id="a1912-242">21847</span></span>|<span data-ttu-id="a1912-243">User</span><span class="sxs-lookup"><span data-stu-id="a1912-243">User</span></span>|  
|<span data-ttu-id="a1912-244">22099</span><span class="sxs-lookup"><span data-stu-id="a1912-244">22099</span></span>|<span data-ttu-id="a1912-245">Service Broker サービス</span><span class="sxs-lookup"><span data-stu-id="a1912-245">Service Broker Service</span></span>|  
|<span data-ttu-id="a1912-246">22601</span><span class="sxs-lookup"><span data-stu-id="a1912-246">22601</span></span>|<span data-ttu-id="a1912-247">インデックス</span><span class="sxs-lookup"><span data-stu-id="a1912-247">Index</span></span>|  
|<span data-ttu-id="a1912-248">22604</span><span class="sxs-lookup"><span data-stu-id="a1912-248">22604</span></span>|<span data-ttu-id="a1912-249">証明書ログイン</span><span class="sxs-lookup"><span data-stu-id="a1912-249">Certificate Login</span></span>|  
|<span data-ttu-id="a1912-250">22611</span><span class="sxs-lookup"><span data-stu-id="a1912-250">22611</span></span>|<span data-ttu-id="a1912-251">XMLSchema</span><span class="sxs-lookup"><span data-stu-id="a1912-251">XMLSchema</span></span>|  
|<span data-ttu-id="a1912-252">22868</span><span class="sxs-lookup"><span data-stu-id="a1912-252">22868</span></span>|<span data-ttu-id="a1912-253">Type</span><span class="sxs-lookup"><span data-stu-id="a1912-253">Type</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1912-254">参照</span><span class="sxs-lookup"><span data-stu-id="a1912-254">See Also</span></span>  
 [<span data-ttu-id="a1912-255">sp_trace_setevent &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a1912-255">sp_trace_setevent &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
