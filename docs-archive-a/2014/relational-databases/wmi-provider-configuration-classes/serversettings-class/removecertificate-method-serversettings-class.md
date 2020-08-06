---
title: RemoveCertificate メソッド (ServerSettings クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- RemoveCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- RemoveCertificate method
ms.assetid: 9ffdbc39-93f5-48fb-859a-86a3ad545827
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 00731fab5c4bdec61848df93829dd5013a7454f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712917"
---
# <a name="removecertificate-method-serversettings-class"></a><span data-ttu-id="0cc2e-102">RemoveCertificate メソッド (ServerSettings クラス)</span><span class="sxs-lookup"><span data-stu-id="0cc2e-102">RemoveCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="0cc2e-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスから現在のセキュリティ証明書を削除します。</span><span class="sxs-lookup"><span data-stu-id="0cc2e-103">Removes the current security certificate from the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cc2e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0cc2e-104">Syntax</span></span>  
  
```  
  
object  
.RemoveCertificate()  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0cc2e-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="0cc2e-105">Parts</span></span>  
 <span data-ttu-id="0cc2e-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0cc2e-106">*object*</span></span>  
 <span data-ttu-id="0cc2e-107">[のインスタンス上のサーバー設定を表す](serversettings-class.md) ServerSettings クラス [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0cc2e-107">A [ServerSettings Class](serversettings-class.md) object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0cc2e-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="0cc2e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="0cc2e-109">u`int32` 値。サービスが正常に変更された場合は 0、要求がサポートされない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="0cc2e-109">A u`int32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cc2e-110">解説</span><span class="sxs-lookup"><span data-stu-id="0cc2e-110">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc2e-111">参照</span><span class="sxs-lookup"><span data-stu-id="0cc2e-111">See Also</span></span>  
 <span data-ttu-id="0cc2e-112">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0cc2e-112">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
