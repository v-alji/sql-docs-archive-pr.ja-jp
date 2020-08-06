---
title: GetCurrentCertificate メソッド (ServerSettings クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- GetCurrentCertificate Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- GetCurrentCertificate method
ms.assetid: 450e33c6-91d4-420f-ab7c-1905111f5658
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b36a5fe7cd39da0f336d05fc4c450170fa21199d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712938"
---
# <a name="getcurrentcertificate-method-serversettings-class"></a><span data-ttu-id="9f923-102">GetCurrentCertificate メソッド (ServerSettings クラス)</span><span class="sxs-lookup"><span data-stu-id="9f923-102">GetCurrentCertificate Method (ServerSettings Class)</span></span>
  <span data-ttu-id="9f923-103">現在のセキュリティ証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f923-103">Gets the current security certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f923-104">構文</span><span class="sxs-lookup"><span data-stu-id="9f923-104">Syntax</span></span>  
  
```  
  
object  
.GetCurrentCertificate(  
SHA  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="9f923-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="9f923-105">Parts</span></span>  
 <span data-ttu-id="9f923-106">*object*</span><span class="sxs-lookup"><span data-stu-id="9f923-106">*object*</span></span>  
 <span data-ttu-id="9f923-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上のサーバー設定を表す `ServerSettings` オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9f923-107">A `ServerSettings` object that represents the server settings on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="9f923-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f923-108">Parameters</span></span>  
  
|<span data-ttu-id="9f923-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f923-109">Parameter</span></span>|<span data-ttu-id="9f923-110">説明</span><span class="sxs-lookup"><span data-stu-id="9f923-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f923-111">*SHA*</span><span class="sxs-lookup"><span data-stu-id="9f923-111">*SHA*</span></span>|<span data-ttu-id="9f923-112">メソッドの完了後に現在のセキュリティ証明書を指定する文字列オブジェクトの値 (出力パラメーター)</span><span class="sxs-lookup"><span data-stu-id="9f923-112">A string object value (output parameter) that specifies the current security certificate after the method completes.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="9f923-113">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="9f923-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="9f923-114">`uint32` 値。サービスが正常に変更された場合は 0、要求がサポートされていない場合は 1 になります。それ以外の数値はエラーを示します。</span><span class="sxs-lookup"><span data-stu-id="9f923-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f923-115">解説</span><span class="sxs-lookup"><span data-stu-id="9f923-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f923-116">参照</span><span class="sxs-lookup"><span data-stu-id="9f923-116">See Also</span></span>  
 <span data-ttu-id="9f923-117">[サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="9f923-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
