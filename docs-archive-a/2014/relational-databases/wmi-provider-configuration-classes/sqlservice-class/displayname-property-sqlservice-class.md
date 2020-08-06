---
title: DisplayName プロパティ (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- DisplayName Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- DisplayName property
ms.assetid: 49c408aa-6eb4-45cd-8d5c-60f065f24f5c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 147fc298d6d263caf1e4ad6852d4b02f86911572
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738112"
---
# <a name="displayname-property-sqlservice-class"></a><span data-ttu-id="c0b1e-102">DisplayName プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="c0b1e-102">DisplayName Property (SqlService Class)</span></span>
  <span data-ttu-id="c0b1e-103">サービスの表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="c0b1e-103">Gets the display name of the service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b1e-104">構文</span><span class="sxs-lookup"><span data-stu-id="c0b1e-104">Syntax</span></span>  
  
```  
  
object  
.DisplayName [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="c0b1e-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c0b1e-105">Parts</span></span>  
 <span data-ttu-id="c0b1e-106">*object*</span><span class="sxs-lookup"><span data-stu-id="c0b1e-106">*object*</span></span>  
 <span data-ttu-id="c0b1e-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c0b1e-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="c0b1e-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="c0b1e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="c0b1e-109">サービスの表示名を指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="c0b1e-109">A string value that specifies the display name of the service.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0b1e-110">解説</span><span class="sxs-lookup"><span data-stu-id="c0b1e-110">Remarks</span></span>  
 <span data-ttu-id="c0b1e-111">この文字列の長さは最大 256 文字です。</span><span class="sxs-lookup"><span data-stu-id="c0b1e-111">This string has a maximum length of 256 characters.</span></span> <span data-ttu-id="c0b1e-112">名前は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="c0b1e-112">The name is case-preserved in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager.</span></span> <span data-ttu-id="c0b1e-113">ただし、表示名の比較時には、常に大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="c0b1e-113">However, display name comparisons are always case-insensitive.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0b1e-114">例</span><span class="sxs-lookup"><span data-stu-id="c0b1e-114">Example</span></span>  
  
```  
mysqlservice.DisplayName = "Atdisk"  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0b1e-115">参照</span><span class="sxs-lookup"><span data-stu-id="c0b1e-115">See Also</span></span>  
 <span data-ttu-id="c0b1e-116">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c0b1e-116">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
