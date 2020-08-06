---
title: ExitCode プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ExitCode Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ExitCode property
ms.assetid: e6b8bff2-946f-4abe-bd50-1f7bb11fdddf
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: f7f5414afd8507a1fc9c592d6b8226692e9683a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634337"
---
# <a name="exitcode-property-sqlservice-class"></a><span data-ttu-id="f0eab-102">ExitCode プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="f0eab-102">ExitCode Property (SqlService Class)</span></span>
  <span data-ttu-id="f0eab-103">サービスの開始時および停止時に検出される問題を定義した [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 エラー コードを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="f0eab-103">Gets or sets the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Win32 error code that defines problems encountered when starting and stopping the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0eab-104">構文</span><span class="sxs-lookup"><span data-stu-id="f0eab-104">Syntax</span></span>  
  
```  
  
object  
.ExitCode [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="f0eab-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="f0eab-105">Parts</span></span>  
 <span data-ttu-id="f0eab-106">*object*</span><span class="sxs-lookup"><span data-stu-id="f0eab-106">*object*</span></span>  
 <span data-ttu-id="f0eab-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="f0eab-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="f0eab-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="f0eab-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="f0eab-109">終了コードを指定する `uint32` 値。</span><span class="sxs-lookup"><span data-stu-id="f0eab-109">A `uint32` value that specifies the exit code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0eab-110">解説</span><span class="sxs-lookup"><span data-stu-id="f0eab-110">Remarks</span></span>  
 <span data-ttu-id="f0eab-111">このプロパティは、エラーがこのクラスによって表されているサービスに特有な場合には、ERROR_SERVICE_SPECIFIC_ERROR (1066) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0eab-111">This property is set to ERROR_SERVICE_SPECIFIC_ERROR (1066) when the error is unique to the service represented by this class.</span></span> <span data-ttu-id="f0eab-112">サービスは、実行時にこの値を NO_ERROR に設定し、通常終了時にも再度設定します。</span><span class="sxs-lookup"><span data-stu-id="f0eab-112">The service sets this value to NO_ERROR when running, and again upon normal termination.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0eab-113">参照</span><span class="sxs-lookup"><span data-stu-id="f0eab-113">See Also</span></span>  
 <span data-ttu-id="f0eab-114">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f0eab-114">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
