---
title: SetDefaults メソッド (CInstance クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (CInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: ed9e99c2-3e28-4ee8-bc20-61ca05984973
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5e589796f973592d7f9f549bffbbf8dfbe49cc27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630839"
---
# <a name="setdefaults-method-cinstance-class"></a><span data-ttu-id="712fc-102">SetDefaults メソッド (CInstance クラス)</span><span class="sxs-lookup"><span data-stu-id="712fc-102">SetDefaults Method (CInstance Class)</span></span>
  <span data-ttu-id="712fc-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 既存のデータを上書きするオプションを使用して、クライアントのインスタンスのすべての既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="712fc-103">Sets all the default values for the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="712fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="712fc-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="712fc-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="712fc-105">Parts</span></span>  
 <span data-ttu-id="712fc-106">*object*</span><span class="sxs-lookup"><span data-stu-id="712fc-106">*object*</span></span>  
 <span data-ttu-id="712fc-107">[クライアント インスタンスを表す](cinstance-class.md) CInstance クラス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="712fc-107">A [CInstance Class](cinstance-class.md) object that represents a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="712fc-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="712fc-108">Parameters</span></span>  
  
|<span data-ttu-id="712fc-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="712fc-109">Parameter</span></span>|<span data-ttu-id="712fc-110">説明</span><span class="sxs-lookup"><span data-stu-id="712fc-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="712fc-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="712fc-111">*OverwriteAll*</span></span>|<span data-ttu-id="712fc-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントのインスタンス上の既存の値を上書きするかどうかを指定するブール値。既存のデータを上書きするには `true`、既存のデータを上書きしない場合は `false` を指定します。</span><span class="sxs-lookup"><span data-stu-id="712fc-112">A Boolean value that specifies whether to overwrite existing values on the instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client: `true` to overwrite existing data, or `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="712fc-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="712fc-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="712fc-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="712fc-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="712fc-115">解説</span><span class="sxs-lookup"><span data-stu-id="712fc-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="712fc-116">参照</span><span class="sxs-lookup"><span data-stu-id="712fc-116">See Also</span></span>  
 [<span data-ttu-id="712fc-117">クライアント プロトコルの構成</span><span class="sxs-lookup"><span data-stu-id="712fc-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
