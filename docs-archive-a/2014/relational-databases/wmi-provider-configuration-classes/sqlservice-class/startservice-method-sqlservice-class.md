---
title: StartService メソッド (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- StartService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- StartService method
ms.assetid: 83dfb6bd-dbd5-45d8-aad2-a11926317f91
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4d91646da2ac2c9f636655ff6c65808ba115e28f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717612"
---
# <a name="startservice-method-sqlservice-class"></a><span data-ttu-id="9e889-102">StartService メソッド (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="9e889-102">StartService Method (SqlService Class)</span></span>
  <span data-ttu-id="9e889-103">サービスを開始状態にする動作を試行します。</span><span class="sxs-lookup"><span data-stu-id="9e889-103">Attempts to place the service into its started state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e889-104">構文</span><span class="sxs-lookup"><span data-stu-id="9e889-104">Syntax</span></span>  
  
```  
  
object  
.StartService()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="9e889-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9e889-105">Parts</span></span>  
 <span data-ttu-id="9e889-106">*object*</span><span class="sxs-lookup"><span data-stu-id="9e889-106">*object*</span></span>  
 <span data-ttu-id="9e889-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9e889-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9e889-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="9e889-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="9e889-109">次のスタートアップ状態のうちの 1 つを指定する uint32 値。</span><span class="sxs-lookup"><span data-stu-id="9e889-109">A uint32 value that specifies one of the following startup states.</span></span>  
  
 <span data-ttu-id="9e889-110">0</span><span class="sxs-lookup"><span data-stu-id="9e889-110">0</span></span>  
 <span data-ttu-id="9e889-111">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="9e889-111">Success.</span></span> <span data-ttu-id="9e889-112">要求が受け入れられました。</span><span class="sxs-lookup"><span data-stu-id="9e889-112">The request was accepted.</span></span>  
  
 <span data-ttu-id="9e889-113">1</span><span class="sxs-lookup"><span data-stu-id="9e889-113">1</span></span>  
 <span data-ttu-id="9e889-114">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9e889-114">Not Supported.</span></span> <span data-ttu-id="9e889-115">要求はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="9e889-115">The request is not supported.</span></span>  
  
 <span data-ttu-id="9e889-116">2</span><span class="sxs-lookup"><span data-stu-id="9e889-116">2</span></span>  
 <span data-ttu-id="9e889-117">アクセスが拒否されました。</span><span class="sxs-lookup"><span data-stu-id="9e889-117">Access Denied.</span></span> <span data-ttu-id="9e889-118">ユーザーには適切なアクセス権がありませんでした。</span><span class="sxs-lookup"><span data-stu-id="9e889-118">The user did not have appropriate access.</span></span>  
  
 <span data-ttu-id="9e889-119">3</span><span class="sxs-lookup"><span data-stu-id="9e889-119">3</span></span>  
 <span data-ttu-id="9e889-120">依存サービス実行中。</span><span class="sxs-lookup"><span data-stu-id="9e889-120">Dependent Services Running.</span></span> <span data-ttu-id="9e889-121">そのサービスは、実行中の他のサービスが依存しているので停止できません。</span><span class="sxs-lookup"><span data-stu-id="9e889-121">The service cannot be stopped because other services that are running are dependent on it.</span></span>  
  
 <span data-ttu-id="9e889-122">4</span><span class="sxs-lookup"><span data-stu-id="9e889-122">4</span></span>  
 <span data-ttu-id="9e889-123">無効なサービス コントロール。</span><span class="sxs-lookup"><span data-stu-id="9e889-123">Invalid Service Control.</span></span> <span data-ttu-id="9e889-124">要求された制御コードは有効でないか、またはサービスを受け入れ可能ではありません。</span><span class="sxs-lookup"><span data-stu-id="9e889-124">The requested control code is not valid, or it is unacceptable to the service.</span></span>  
  
 <span data-ttu-id="9e889-125">5</span><span class="sxs-lookup"><span data-stu-id="9e889-125">5</span></span>  
 <span data-ttu-id="9e889-126">サービスは制御を受け付けられません。</span><span class="sxs-lookup"><span data-stu-id="9e889-126">Service Cannot Accept Control.</span></span> <span data-ttu-id="9e889-127">サービスの状態 (Win32_BaseService:State) が 0、1、または 2 と等しいので、要求された制御コードはサービスに送信されませんでした。</span><span class="sxs-lookup"><span data-stu-id="9e889-127">The requested control code cannot be sent to the service because the state of the service (Win32_BaseService:State) is equal to 0, 1, or 2.</span></span>  
  
 <span data-ttu-id="9e889-128">6</span><span class="sxs-lookup"><span data-stu-id="9e889-128">6</span></span>  
 <span data-ttu-id="9e889-129">サービスはアクティブではありません。</span><span class="sxs-lookup"><span data-stu-id="9e889-129">Service Not Active.</span></span> <span data-ttu-id="9e889-130">サービスは開始されていません。</span><span class="sxs-lookup"><span data-stu-id="9e889-130">The service has not been started.</span></span>  
  
 <span data-ttu-id="9e889-131">7</span><span class="sxs-lookup"><span data-stu-id="9e889-131">7</span></span>  
 <span data-ttu-id="9e889-132">サービス要求タイムアウト。</span><span class="sxs-lookup"><span data-stu-id="9e889-132">Service Request Timeout.</span></span> <span data-ttu-id="9e889-133">サービスは適切な時間内に開始要求に応答しませんでした。</span><span class="sxs-lookup"><span data-stu-id="9e889-133">The service did not respond to the start request in a timely fashion.</span></span>  
  
 <span data-ttu-id="9e889-134">8</span><span class="sxs-lookup"><span data-stu-id="9e889-134">8</span></span>  
 <span data-ttu-id="9e889-135">不明なエラーです。</span><span class="sxs-lookup"><span data-stu-id="9e889-135">Unknown Failure.</span></span> <span data-ttu-id="9e889-136">サービスの開始時に不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9e889-136">An unknown failure occurred when starting the service.</span></span>  
  
 <span data-ttu-id="9e889-137">9</span><span class="sxs-lookup"><span data-stu-id="9e889-137">9</span></span>  
 <span data-ttu-id="9e889-138">パスが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="9e889-138">Path Not Found.</span></span> <span data-ttu-id="9e889-139">サービス実行可能ファイルへのディレクトリ パスが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="9e889-139">The directory path to the service executable was not found.</span></span>  
  
 <span data-ttu-id="9e889-140">10</span><span class="sxs-lookup"><span data-stu-id="9e889-140">10</span></span>  
 <span data-ttu-id="9e889-141">サービスは既に実行中です。</span><span class="sxs-lookup"><span data-stu-id="9e889-141">Service Already Running.</span></span> <span data-ttu-id="9e889-142">サービスは既に実行されています。</span><span class="sxs-lookup"><span data-stu-id="9e889-142">The service is already running.</span></span>  
  
 <span data-ttu-id="9e889-143">11</span><span class="sxs-lookup"><span data-stu-id="9e889-143">11</span></span>  
 <span data-ttu-id="9e889-144">サービス データベースはロックされています。</span><span class="sxs-lookup"><span data-stu-id="9e889-144">Service Database Locked.</span></span> <span data-ttu-id="9e889-145">新しいサービスを追加するデータベースはロックされています。</span><span class="sxs-lookup"><span data-stu-id="9e889-145">The database to add a new service is locked.</span></span>  
  
 <span data-ttu-id="9e889-146">12</span><span class="sxs-lookup"><span data-stu-id="9e889-146">12</span></span>  
 <span data-ttu-id="9e889-147">サービス依存は削除されました。</span><span class="sxs-lookup"><span data-stu-id="9e889-147">Service Dependency Deleted.</span></span> <span data-ttu-id="9e889-148">このサービスが依存する依存関係はシステムから削除されました。</span><span class="sxs-lookup"><span data-stu-id="9e889-148">A dependency on which this service relies has been removed from the system.</span></span>  
  
 <span data-ttu-id="9e889-149">13</span><span class="sxs-lookup"><span data-stu-id="9e889-149">13</span></span>  
 <span data-ttu-id="9e889-150">サービス依存エラー。</span><span class="sxs-lookup"><span data-stu-id="9e889-150">Service Dependency Failure.</span></span> <span data-ttu-id="9e889-151">サービスは依存関係のあるサービスから必要なサービスを見つけられませんでした。</span><span class="sxs-lookup"><span data-stu-id="9e889-151">The service failed to find the service needed from a dependent service.</span></span>  
  
 <span data-ttu-id="9e889-152">14</span><span class="sxs-lookup"><span data-stu-id="9e889-152">14</span></span>  
 <span data-ttu-id="9e889-153">無効なサービス。</span><span class="sxs-lookup"><span data-stu-id="9e889-153">Service Disabled.</span></span> <span data-ttu-id="9e889-154">サービスはシステムから無効になっています。</span><span class="sxs-lookup"><span data-stu-id="9e889-154">The service has been disabled from the system.</span></span>  
  
 <span data-ttu-id="9e889-155">15</span><span class="sxs-lookup"><span data-stu-id="9e889-155">15</span></span>  
 <span data-ttu-id="9e889-156">サービス ログオンに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9e889-156">Service Logon Failed.</span></span> <span data-ttu-id="9e889-157">サービスにはシステムで実行するための正しい認証がありません。</span><span class="sxs-lookup"><span data-stu-id="9e889-157">The service does not have the correct authentication to run on the system.</span></span>  
  
 <span data-ttu-id="9e889-158">16</span><span class="sxs-lookup"><span data-stu-id="9e889-158">16</span></span>  
 <span data-ttu-id="9e889-159">サービスは削除をマークしました。</span><span class="sxs-lookup"><span data-stu-id="9e889-159">Service Marked For Deletion.</span></span> <span data-ttu-id="9e889-160">サービスはシステムから削除されています。</span><span class="sxs-lookup"><span data-stu-id="9e889-160">The service is being removed from the system.</span></span>  
  
 <span data-ttu-id="9e889-161">17</span><span class="sxs-lookup"><span data-stu-id="9e889-161">17</span></span>  
 <span data-ttu-id="9e889-162">サービス スレッドなし。</span><span class="sxs-lookup"><span data-stu-id="9e889-162">Service No Thread.</span></span> <span data-ttu-id="9e889-163">サービスに実行スレッドがありません。</span><span class="sxs-lookup"><span data-stu-id="9e889-163">There is no execution thread for the service.</span></span>  
  
 <span data-ttu-id="9e889-164">18</span><span class="sxs-lookup"><span data-stu-id="9e889-164">18</span></span>  
 <span data-ttu-id="9e889-165">状態循環依存。</span><span class="sxs-lookup"><span data-stu-id="9e889-165">Status Circular Dependency.</span></span> <span data-ttu-id="9e889-166">サービスの開始時に循環依存があります。</span><span class="sxs-lookup"><span data-stu-id="9e889-166">There are circular dependencies when starting the service.</span></span>  
  
 <span data-ttu-id="9e889-167">19</span><span class="sxs-lookup"><span data-stu-id="9e889-167">19</span></span>  
 <span data-ttu-id="9e889-168">状態重複名。</span><span class="sxs-lookup"><span data-stu-id="9e889-168">Status Duplicate Name.</span></span> <span data-ttu-id="9e889-169">同じ名前で実行中のサービスがあります。</span><span class="sxs-lookup"><span data-stu-id="9e889-169">There is a service running under the same name.</span></span>  
  
 <span data-ttu-id="9e889-170">20</span><span class="sxs-lookup"><span data-stu-id="9e889-170">20</span></span>  
 <span data-ttu-id="9e889-171">状態無効名。</span><span class="sxs-lookup"><span data-stu-id="9e889-171">Status Invalid Name.</span></span> <span data-ttu-id="9e889-172">サービスの名前に有効ではない文字があります。</span><span class="sxs-lookup"><span data-stu-id="9e889-172">There are characters that are not valid in the name of the service.</span></span>  
  
 <span data-ttu-id="9e889-173">21</span><span class="sxs-lookup"><span data-stu-id="9e889-173">21</span></span>  
 <span data-ttu-id="9e889-174">状態無効パラメーター。</span><span class="sxs-lookup"><span data-stu-id="9e889-174">Status Invalid Parameter.</span></span> <span data-ttu-id="9e889-175">有効ではないパラメーターがサービスに渡されました。</span><span class="sxs-lookup"><span data-stu-id="9e889-175">Parameters that are not valid have been passed to the service.</span></span>  
  
 <span data-ttu-id="9e889-176">22</span><span class="sxs-lookup"><span data-stu-id="9e889-176">22</span></span>  
 <span data-ttu-id="9e889-177">状態無効サービス アカウント。</span><span class="sxs-lookup"><span data-stu-id="9e889-177">Status Invalid Service Account.</span></span> <span data-ttu-id="9e889-178">このサービスを実行しようとしているアカウントは無効か、またはサービスを実行する権限がありません。</span><span class="sxs-lookup"><span data-stu-id="9e889-178">The account which this service is to run under is not valid, or it lacks the permissions to run the service.</span></span>  
  
 <span data-ttu-id="9e889-179">23</span><span class="sxs-lookup"><span data-stu-id="9e889-179">23</span></span>  
 <span data-ttu-id="9e889-180">状態サービスが存在します。</span><span class="sxs-lookup"><span data-stu-id="9e889-180">Status Service Exists.</span></span> <span data-ttu-id="9e889-181">サービスは、システムから利用できるサービスのデータベースにあります。</span><span class="sxs-lookup"><span data-stu-id="9e889-181">The service exists in the database of services available from the system.</span></span>  
  
 <span data-ttu-id="9e889-182">24</span><span class="sxs-lookup"><span data-stu-id="9e889-182">24</span></span>  
 <span data-ttu-id="9e889-183">サービスは既に一時停止しています。</span><span class="sxs-lookup"><span data-stu-id="9e889-183">Service Already Paused.</span></span> <span data-ttu-id="9e889-184">サービスは現在システムで一時停止されています。</span><span class="sxs-lookup"><span data-stu-id="9e889-184">The service is currently paused in the system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e889-185">解説</span><span class="sxs-lookup"><span data-stu-id="9e889-185">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e889-186">参照</span><span class="sxs-lookup"><span data-stu-id="9e889-186">See Also</span></span>  
 <span data-ttu-id="9e889-187">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9e889-187">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
