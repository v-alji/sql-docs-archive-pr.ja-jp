---
title: SetDefaults メソッド (ServerSettings クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 93dd2eee5a395d4d7463ebf9b85530fcf82d1888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715113"
---
# <a name="setdefaults-method-serversettings-class"></a><span data-ttu-id="a8015-102">SetDefaults メソッド (ServerSettings クラス)</span><span class="sxs-lookup"><span data-stu-id="a8015-102">SetDefaults Method (ServerSettings Class)</span></span>
  <span data-ttu-id="a8015-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 既存のデータを上書きするオプションを使用して、のインスタンスのすべての既定値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a8015-103">Sets all the default values for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8015-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8015-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="a8015-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="a8015-105">Parts</span></span>  
 <span data-ttu-id="a8015-106">*object*</span><span class="sxs-lookup"><span data-stu-id="a8015-106">*object*</span></span>  
 <span data-ttu-id="a8015-107">クライアントインスタンスを表す[Serversettings クラス](serversettings-class.md)オブジェクト [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a8015-107">A [ServerSettings Class](serversettings-class.md) object that represents a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="a8015-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8015-108">Parameters</span></span>  
  
|<span data-ttu-id="a8015-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8015-109">Parameter</span></span>|<span data-ttu-id="a8015-110">説明</span><span class="sxs-lookup"><span data-stu-id="a8015-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a8015-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="a8015-111">*OverwriteAll*</span></span>|<span data-ttu-id="a8015-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上の既存の値を上書きするかどうかを指定するブール値。既存のデータを上書きするには `true`、既存のデータを上書きしない場合は `false` を指定します。</span><span class="sxs-lookup"><span data-stu-id="a8015-112">A Boolean value that specifies whether to overwrite existing values on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]: `true` to overwrite existing data, or `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="a8015-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="a8015-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="a8015-114">u`int32` 値。サービスが正常に変更された場合は 0、要求がサポートされない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="a8015-114">A u`int32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8015-115">解説</span><span class="sxs-lookup"><span data-stu-id="a8015-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8015-116">参照</span><span class="sxs-lookup"><span data-stu-id="a8015-116">See Also</span></span>  
 <span data-ttu-id="a8015-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="a8015-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
