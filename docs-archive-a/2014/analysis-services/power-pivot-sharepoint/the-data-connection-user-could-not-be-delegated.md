---
title: 'データ接続では Windows 認証を使用しており、ユーザーの資格情報を借用できませんでした。 次の接続を更新できませんでした: PowerPivot Data |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
author: minewiskan
ms.author: owend
ms.openlocfilehash: be4c61ad4514f3aa4f6f1eda1fe44ad97c4c064f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634706"
---
# <a name="the-data-connection-uses-windows-authentication-and-user-credentials-could-not-be-delegated-the-following-connections-failed-to-refresh-powerpivot-data"></a><span data-ttu-id="6b288-103">データ接続では Windows 認証を使用しており、ユーザーの資格情報を借用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="6b288-103">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="6b288-104">次の接続の更新に失敗しました:PowerPivot データ</span><span class="sxs-lookup"><span data-stu-id="6b288-104">The following connections failed to refresh: PowerPivot Data</span></span>
  <span data-ttu-id="6b288-105">PowerPivot データを含む Excel ブックで、Excel Services は、SharePoint の PowerPivot サーバー インスタンスに接続できない場合にこのエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="6b288-105">For Excel workbooks that contain PowerPivot data, Excel Services returns this error if it cannot connect to a PowerPivot server instance in SharePoint.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6b288-106">詳細</span><span class="sxs-lookup"><span data-stu-id="6b288-106">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b288-107">適用対象</span><span class="sxs-lookup"><span data-stu-id="6b288-107">Applies to</span></span>|<span data-ttu-id="6b288-108">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="6b288-108">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="6b288-109">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="6b288-109">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="6b288-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b288-110">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="6b288-111">原因</span><span class="sxs-lookup"><span data-stu-id="6b288-111">Cause</span></span>|<span data-ttu-id="6b288-112">PowerPivot データ プロバイダーを使用しようとしたときに接続が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="6b288-112">Connection failed when attempting to use a PowerPivot data provider.</span></span>|  
|<span data-ttu-id="6b288-113">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="6b288-113">Message Text</span></span>|<span data-ttu-id="6b288-114">データ接続では Windows 認証を使用しており、ユーザーの資格情報を借用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="6b288-114">The data connection uses Windows Authentication and user credentials could not be delegated.</span></span> <span data-ttu-id="6b288-115">次の接続の更新に失敗しました:PowerPivot データ</span><span class="sxs-lookup"><span data-stu-id="6b288-115">The following connections failed to refresh: PowerPivot Data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6b288-116">説明</span><span class="sxs-lookup"><span data-stu-id="6b288-116">Explanation</span></span>  
 <span data-ttu-id="6b288-117">このエラー メッセージには複数の原因があります。</span><span class="sxs-lookup"><span data-stu-id="6b288-117">There are multiple causes for this error message.</span></span> <span data-ttu-id="6b288-118">それらの原因に共通する要因は、Excel Services が SharePoint のクレーム トークンから有効な Windows ユーザー ID を取得できないことです。</span><span class="sxs-lookup"><span data-stu-id="6b288-118">The common factor behind all of them is that Excel Services cannot get a valid Windows user identity from a claims token in SharePoint.</span></span> <span data-ttu-id="6b288-119">PowerPivot データを含む Excel ブックの場合、次のいずれかの条件に当てはまるときは、このエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6b288-119">In the case of Excel workbooks that contain PowerPivot data, this error occurs when any of the following conditions exist:</span></span>  
  
-   <span data-ttu-id="6b288-120">Windows トークン サービスに対するクレームが実行されていない。</span><span class="sxs-lookup"><span data-stu-id="6b288-120">The Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="6b288-121">SharePoint ログ ファイルを表示して、このエラーの原因を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6b288-121">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="6b288-122">SharePoint ログに、"パイプ エンドポイント 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' が、ローカル コンピューター上で見つかりませんでした" というメッセージがある場合、Windows トークン サービスに対するクレームは実行されていません。</span><span class="sxs-lookup"><span data-stu-id="6b288-122">If the SharePoint logs include the message "The pipe endpoint 'net.pipe://localhost/s4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' could not be found on your local machine", the Claims to Windows Token Service is not running.</span></span> <span data-ttu-id="6b288-123">このサービスを開始するには、サーバーの全体管理を使用します。その後、[サービス] コンソール アプリケーションでサービスが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6b288-123">To start it, use Central Administration and then verify the service is running in the Services console application.</span></span>  
  
-   <span data-ttu-id="6b288-124">ユーザー ID の検証にドメイン コントローラーを使用できない。</span><span class="sxs-lookup"><span data-stu-id="6b288-124">A domain controller is not available to validate the user identity.</span></span> <span data-ttu-id="6b288-125">Windows トークン サービスに対するクレームでは、キャッシュされた資格情報は使用されません。</span><span class="sxs-lookup"><span data-stu-id="6b288-125">The Claims to Windows Token Service does not use cached credentials.</span></span> <span data-ttu-id="6b288-126">接続ごとにユーザー ID が検証されます。</span><span class="sxs-lookup"><span data-stu-id="6b288-126">It validates the user identity for each connection.</span></span> <span data-ttu-id="6b288-127">SharePoint ログ ファイルを表示して、このエラーの原因を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6b288-127">You can confirm the cause of this error by viewing the SharePoint log file.</span></span> <span data-ttu-id="6b288-128">SharePoint ログに、"IClaimsIdentity から WindowsIdentity を取得できませんでした" というメッセージがある場合、ユーザー ID を認証できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="6b288-128">If the SharePoint logs include the message "Failed to get WindowsIdentity from IClaimsIdentity", the user identity could not be authenticated.</span></span>  
  
-   <span data-ttu-id="6b288-129">コンピューターは同じドメインまたは双方向の信頼関係を持つドメインのメンバーである必要がある。</span><span class="sxs-lookup"><span data-stu-id="6b288-129">The computers must be members of the same domain or in domains that have a two-way trust relationship.</span></span>  
  
-   <span data-ttu-id="6b288-130">Windows ドメイン ユーザー アカウントを使用する必要がある。</span><span class="sxs-lookup"><span data-stu-id="6b288-130">You must use Windows domain user accounts.</span></span> <span data-ttu-id="6b288-131">これらのアカウントにはユニバーサル プリンシパル名 (UPN) が必要です。</span><span class="sxs-lookup"><span data-stu-id="6b288-131">The accounts must have a Universal Principal Name (UPN).</span></span>  
  
-   <span data-ttu-id="6b288-132">オブジェクトを照会するために、Excel Services サービス アカウントに Active Directory のアクセス許可が必要である。</span><span class="sxs-lookup"><span data-stu-id="6b288-132">The Excel Services service account must have Active Directory permissions to query the object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6b288-133">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="6b288-133">User Action</span></span>  
 <span data-ttu-id="6b288-134">次の手順に従って、Windows トークン サービスに対するクレームの状態を確認します。</span><span class="sxs-lookup"><span data-stu-id="6b288-134">Use the following instructions to check the status of the Claims to Windows Token Service.</span></span>  
  
 <span data-ttu-id="6b288-135">その他の場合については、ネットワーク管理者に確認してください。</span><span class="sxs-lookup"><span data-stu-id="6b288-135">For all other scenarios, check with your network administrator.</span></span>  
  
#### <a name="enable-claims-to-windows-token-service"></a><span data-ttu-id="6b288-136">Windows トークン サービスに対するクレームの有効化</span><span class="sxs-lookup"><span data-stu-id="6b288-136">Enable Claims to Windows Token Service</span></span>  
  
1.  <span data-ttu-id="6b288-137">サーバーの全体管理で、[システム設定] の [**サーバーのサービスの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b288-137">In Central Administration, in System Settings, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="6b288-138">**[Windows トークン サービスに対するクレーム]** を選択し、 **[開始]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b288-138">Select **Claims to Windows Token Service**, and then click **Start**.</span></span>  
  
3.  <span data-ttu-id="6b288-139">[サービス] コンソールでサービスが実行されていることも確認します。</span><span class="sxs-lookup"><span data-stu-id="6b288-139">Verify the service is also running in the Services console:</span></span>  
  
    1.  <span data-ttu-id="6b288-140">[管理ツール] で、[サービス] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b288-140">In Administrative Tools, click Services.</span></span>  
  
    2.  <span data-ttu-id="6b288-141">Windows トークン サービスに対するクレームが実行されていない場合は開始します。</span><span class="sxs-lookup"><span data-stu-id="6b288-141">Start the Claims to Windows Token Service if it is not running.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b288-142">参照</span><span class="sxs-lookup"><span data-stu-id="6b288-142">See Also</span></span>  
 [<span data-ttu-id="6b288-143">PowerPivot サービス アカウントの構成</span><span class="sxs-lookup"><span data-stu-id="6b288-143">Configure PowerPivot Service Accounts</span></span>](configure-power-pivot-service-accounts.md)  
  
  
