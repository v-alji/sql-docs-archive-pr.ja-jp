---
title: SetDefaults メソッド (ClientSettings クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ClientSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b6985ebfa4a9145dd3474cec31f32cdab9c11cdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644858"
---
# <a name="setdefaults-method-clientsettings-class"></a><span data-ttu-id="12b64-102">SetDefaults メソッド (ClientSettings クラス)</span><span class="sxs-lookup"><span data-stu-id="12b64-102">SetDefaults Method (ClientSettings Class)</span></span>
  <span data-ttu-id="12b64-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 既存のデータを上書きするオプションを使用して、クライアントのインスタンスのすべての既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="12b64-103">Sets all the default values for the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b64-104">構文</span><span class="sxs-lookup"><span data-stu-id="12b64-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="12b64-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="12b64-105">Parts</span></span>  
 <span data-ttu-id="12b64-106">*object*</span><span class="sxs-lookup"><span data-stu-id="12b64-106">*object*</span></span>  
 <span data-ttu-id="12b64-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアント インスタンスを表す `ClientSettings` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="12b64-107">A `ClientSettings` object that represents a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="12b64-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12b64-108">Parameters</span></span>  
  
|<span data-ttu-id="12b64-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12b64-109">Parameter</span></span>|<span data-ttu-id="12b64-110">説明</span><span class="sxs-lookup"><span data-stu-id="12b64-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12b64-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="12b64-111">*OverwriteAll*</span></span>|<span data-ttu-id="12b64-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントのインスタンス上の既存の値を上書きするかどうかを指定するブール値。</span><span class="sxs-lookup"><span data-stu-id="12b64-112">A Boolean value that specifies whether to overwrite existing values on the instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client.</span></span> <span data-ttu-id="12b64-113">既存のデータを上書きするには `true`、既存のデータを上書きしない場合は `false` を指定します。</span><span class="sxs-lookup"><span data-stu-id="12b64-113">`true` to overwrite existing data; `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="12b64-114">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="12b64-114">Property Value/Return Value</span></span>  
 <span data-ttu-id="12b64-115">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="12b64-115">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12b64-116">解説</span><span class="sxs-lookup"><span data-stu-id="12b64-116">Remarks</span></span>  
  
