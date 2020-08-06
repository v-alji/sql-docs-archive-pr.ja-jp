---
title: SetValue メソッド (ServerSettingsGeneralFlag クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ServerSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 74c4c189b72b7a469794e0828faf062a88cdf46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743129"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a><span data-ttu-id="b3491-102">SetValue メソッド (ServerSettingsGeneralFlag クラス)</span><span class="sxs-lookup"><span data-stu-id="b3491-102">SetValue Method (ServerSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="b3491-103">参照されたフラグのすべての値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b3491-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3491-104">構文</span><span class="sxs-lookup"><span data-stu-id="b3491-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="b3491-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="b3491-105">Parts</span></span>  
 <span data-ttu-id="b3491-106">*object*</span><span class="sxs-lookup"><span data-stu-id="b3491-106">*object*</span></span>  
 <span data-ttu-id="b3491-107">サーバー設定に使用する一般的なフラグを表す [ServerSettingsGeneralFlag クラス](serversettingsgeneralflag-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b3491-107">A [ServerSettingsGeneralFlag Class](serversettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="b3491-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3491-108">Parameters</span></span>  
  
|<span data-ttu-id="b3491-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3491-109">Parameter</span></span>|<span data-ttu-id="b3491-110">説明</span><span class="sxs-lookup"><span data-stu-id="b3491-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3491-111">*Value*</span><span class="sxs-lookup"><span data-stu-id="b3491-111">*Value*</span></span>|<span data-ttu-id="b3491-112">フラグの値を指定するブール値</span><span class="sxs-lookup"><span data-stu-id="b3491-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b3491-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="b3491-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="b3491-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="b3491-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3491-115">解説</span><span class="sxs-lookup"><span data-stu-id="b3491-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3491-116">参照</span><span class="sxs-lookup"><span data-stu-id="b3491-116">See Also</span></span>  
 <span data-ttu-id="b3491-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b3491-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
