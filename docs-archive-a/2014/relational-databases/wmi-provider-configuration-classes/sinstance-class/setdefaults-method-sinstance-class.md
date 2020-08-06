---
title: SetDefaults メソッド (SInstance クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (SInstance Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: dc3c6a85-0711-4688-bf4f-91168c57af28
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: c581834d3c97bed622d16fbb35e48704f8679531
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712910"
---
# <a name="setdefaults-method-sinstance-class"></a><span data-ttu-id="e3b06-102">SetDefaults メソッド (SInstance クラス)</span><span class="sxs-lookup"><span data-stu-id="e3b06-102">SetDefaults Method (SInstance Class)</span></span>
  <span data-ttu-id="e3b06-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 既存のデータを上書きするオプションを使用して、のインスタンスのすべての既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="e3b06-103">Sets all the default values for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3b06-104">構文</span><span class="sxs-lookup"><span data-stu-id="e3b06-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="e3b06-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="e3b06-105">Parts</span></span>  
 <span data-ttu-id="e3b06-106">*object*</span><span class="sxs-lookup"><span data-stu-id="e3b06-106">*object*</span></span>  
 <span data-ttu-id="e3b06-107">サーバーインスタンスを表す[Sinstance クラス](sinstance-class.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="e3b06-107">An [SInstance Class](sinstance-class.md) object that represents a server instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="e3b06-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3b06-108">Parameters</span></span>  
  
|<span data-ttu-id="e3b06-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3b06-109">Parameter</span></span>|<span data-ttu-id="e3b06-110">説明</span><span class="sxs-lookup"><span data-stu-id="e3b06-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3b06-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="e3b06-111">*OverwriteAll*</span></span>|<span data-ttu-id="e3b06-112">クライアントのインスタンスの既存の値を上書きするかどうかを指定するブール値 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。 `true` 既存のデータを上書きする場合は、既存のデータを上書きしない場合はです `false` 。</span><span class="sxs-lookup"><span data-stu-id="e3b06-112">A Boolean value that specifies whether to overwrite existing value on the instance of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client: `true` if existing data is overwritten, or `false` if existing data is not overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e3b06-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="e3b06-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="e3b06-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="e3b06-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3b06-115">解説</span><span class="sxs-lookup"><span data-stu-id="e3b06-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3b06-116">参照</span><span class="sxs-lookup"><span data-stu-id="e3b06-116">See Also</span></span>  
 <span data-ttu-id="e3b06-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="e3b06-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
