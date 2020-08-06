---
title: SetValue メソッド (ClientSettingsGeneralFlag クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ClientSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fffa44bd8743f96a43ca4d1787d8d2afaad5e6cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712981"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a><span data-ttu-id="83cbf-102">SetValue メソッド (ClientSettingsGeneralFlag クラス)</span><span class="sxs-lookup"><span data-stu-id="83cbf-102">SetValue Method (ClientSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="83cbf-103">参照されたフラグのすべての値を設定します。</span><span class="sxs-lookup"><span data-stu-id="83cbf-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83cbf-104">構文</span><span class="sxs-lookup"><span data-stu-id="83cbf-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="83cbf-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="83cbf-105">Parts</span></span>  
 <span data-ttu-id="83cbf-106">*object*</span><span class="sxs-lookup"><span data-stu-id="83cbf-106">*object*</span></span>  
 <span data-ttu-id="83cbf-107">サーバー設定に使用する一般的なフラグを表す [ClientSettingsGeneralFlag クラス](clientsettingsgeneralflag-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="83cbf-107">A [ClientSettingsGeneralFlag Class](clientsettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="83cbf-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83cbf-108">Parameters</span></span>  
  
|<span data-ttu-id="83cbf-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83cbf-109">Parameter</span></span>|<span data-ttu-id="83cbf-110">説明</span><span class="sxs-lookup"><span data-stu-id="83cbf-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="83cbf-111">*Value*</span><span class="sxs-lookup"><span data-stu-id="83cbf-111">*Value*</span></span>|<span data-ttu-id="83cbf-112">フラグの値を指定するブール値</span><span class="sxs-lookup"><span data-stu-id="83cbf-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="83cbf-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="83cbf-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="83cbf-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="83cbf-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83cbf-115">解説</span><span class="sxs-lookup"><span data-stu-id="83cbf-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83cbf-116">参照</span><span class="sxs-lookup"><span data-stu-id="83cbf-116">See Also</span></span>  
 [<span data-ttu-id="83cbf-117">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="83cbf-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
