---
title: ErrorControl プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ErrorControl Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ErrorControl property
ms.assetid: cbb1e0fa-5bfc-4b1b-a6ed-f7d5cfad4d73
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 73c726af514f2880484cf927282fc0e007f07e2c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738106"
---
# <a name="errorcontrol-property-sqlservice-class"></a><span data-ttu-id="026a5-102">ErrorControl プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="026a5-102">ErrorControl Property (SqlService Class)</span></span>
  <span data-ttu-id="026a5-103">起動時にサービスを開始できなかった場合のエラーの重大度を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="026a5-103">Gets or sets the severity of the error if the service fails to start during startup.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="026a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="026a5-104">Syntax</span></span>  
  
```  
  
object  
.ErrorControl [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="026a5-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="026a5-105">Parts</span></span>  
 <span data-ttu-id="026a5-106">*object*</span><span class="sxs-lookup"><span data-stu-id="026a5-106">*object*</span></span>  
 <span data-ttu-id="026a5-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="026a5-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="026a5-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="026a5-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="026a5-109">起動時にサービスが失敗した場合にレポートされるエラーの重大度を指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="026a5-109">A string value that specifies the error severity reported if the service fails during startup.</span></span> <span data-ttu-id="026a5-110">次の表に、それぞれの値を示します。</span><span class="sxs-lookup"><span data-stu-id="026a5-110">The following table shows the possible values.</span></span>  
  
 <span data-ttu-id="026a5-111">無視</span><span class="sxs-lookup"><span data-stu-id="026a5-111">Ignore</span></span>  
 <span data-ttu-id="026a5-112">ユーザーへの通知が行われません。</span><span class="sxs-lookup"><span data-stu-id="026a5-112">User is not notified.</span></span>  
  
 <span data-ttu-id="026a5-113">標準</span><span class="sxs-lookup"><span data-stu-id="026a5-113">Normal</span></span>  
 <span data-ttu-id="026a5-114">ユーザーへの通知が行われます。</span><span class="sxs-lookup"><span data-stu-id="026a5-114">User is notified.</span></span>  
  
 <span data-ttu-id="026a5-115">Severe</span><span class="sxs-lookup"><span data-stu-id="026a5-115">Severe</span></span>  
 <span data-ttu-id="026a5-116">システムは最後の正しい構成で再起動されます。</span><span class="sxs-lookup"><span data-stu-id="026a5-116">System is restarted with the last-known-good configuration.</span></span>  
  
 <span data-ttu-id="026a5-117">重要</span><span class="sxs-lookup"><span data-stu-id="026a5-117">Critical</span></span>  
 <span data-ttu-id="026a5-118">正しい構成でシステムの再起動が試行されます。</span><span class="sxs-lookup"><span data-stu-id="026a5-118">System attempts to restart with a good configuration.</span></span>  
  
 <span data-ttu-id="026a5-119">Unknown</span><span class="sxs-lookup"><span data-stu-id="026a5-119">Unknown</span></span>  
 <span data-ttu-id="026a5-120">重大度が不明です。</span><span class="sxs-lookup"><span data-stu-id="026a5-120">The severity is unknown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="026a5-121">解説</span><span class="sxs-lookup"><span data-stu-id="026a5-121">Remarks</span></span>  
 <span data-ttu-id="026a5-122">値は、失敗が発生した場合に、起動プログラムによって行われるアクションを示しています。</span><span class="sxs-lookup"><span data-stu-id="026a5-122">The value indicates the action taken by the startup program if a failure occurs.</span></span> <span data-ttu-id="026a5-123">すべてのエラーは、コンピューター システムによって記録されます。</span><span class="sxs-lookup"><span data-stu-id="026a5-123">All errors are logged by the computer system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="026a5-124">参照</span><span class="sxs-lookup"><span data-stu-id="026a5-124">See Also</span></span>  
 <span data-ttu-id="026a5-125">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="026a5-125">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
