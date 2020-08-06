---
title: SqlServiceType プロパティ (Sqlserviceadvanced Property クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlServiceAdvancedProperty Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: 20f1663a-9a14-4f14-8c1b-8aa133e272c3
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 774c8599fd21e330fa3228336ab1ed3c73d65c85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645424"
---
# <a name="sqlservicetype-property-sqlserviceadvancedproperty-class"></a><span data-ttu-id="0767e-102">SqlServiceType プロパティ (SqlServiceAdvancedProperty クラス)</span><span class="sxs-lookup"><span data-stu-id="0767e-102">SqlServiceType Property (SqlServiceAdvancedProperty Class)</span></span>
  <span data-ttu-id="0767e-103">詳細プロパティに関連付けられたマネージド サービスの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="0767e-103">Gets the type of the managed service associated with the advanced property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0767e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0767e-104">Syntax</span></span>  
  
```  
  
object  
.SetBoolValue(  
NumValue  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0767e-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="0767e-105">Parts</span></span>  
 <span data-ttu-id="0767e-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0767e-106">*object*</span></span>  
 <span data-ttu-id="0767e-107">詳細プロパティを表す [SqlServiceAdvancedProperty クラス](sqlserviceadvancedproperty-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0767e-107">A [SqlServiceAdvancedProperty Class](sqlserviceadvancedproperty-class.md) object that represents an advanced property.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0767e-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="0767e-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="0767e-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスの種類を指定する uint32 値。</span><span class="sxs-lookup"><span data-stu-id="0767e-109">A uint32 value that specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0767e-110">解説</span><span class="sxs-lookup"><span data-stu-id="0767e-110">Remarks</span></span>  
 <span data-ttu-id="0767e-111">戻り値は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="0767e-111">Return values can be one of the following:</span></span>  
  
|<span data-ttu-id="0767e-112">Type</span><span class="sxs-lookup"><span data-stu-id="0767e-112">Type</span></span>|<span data-ttu-id="0767e-113">定義</span><span class="sxs-lookup"><span data-stu-id="0767e-113">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="0767e-114">*1*</span><span class="sxs-lookup"><span data-stu-id="0767e-114">*1*</span></span>|<span data-ttu-id="0767e-115">MSSQLSERVER は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="0767e-115">MSSQLSERVER is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="0767e-116">*2*</span><span class="sxs-lookup"><span data-stu-id="0767e-116">*2*</span></span>|<span data-ttu-id="0767e-117">SQLSERVERAGENT は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスです。</span><span class="sxs-lookup"><span data-stu-id="0767e-117">SQLSERVERAGENT is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service.</span></span>|  
|<span data-ttu-id="0767e-118">*3*</span><span class="sxs-lookup"><span data-stu-id="0767e-118">*3*</span></span>|<span data-ttu-id="0767e-119">MSFTESQL は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フルテキスト検索エンジン サービスです。</span><span class="sxs-lookup"><span data-stu-id="0767e-119">MSFTESQL is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Full-text Search Engine service.</span></span>|  
|<span data-ttu-id="0767e-120">*4*</span><span class="sxs-lookup"><span data-stu-id="0767e-120">*4*</span></span>|<span data-ttu-id="0767e-121">MsDtsServer は [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="0767e-121">MsDtsServer is the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="0767e-122">*5*</span><span class="sxs-lookup"><span data-stu-id="0767e-122">*5*</span></span>|<span data-ttu-id="0767e-123">MSSQLServerOLAPService は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="0767e-123">MSSQLServerOLAPService is the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="0767e-124">*6*</span><span class="sxs-lookup"><span data-stu-id="0767e-124">*6*</span></span>|<span data-ttu-id="0767e-125">ReportServer は [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="0767e-125">ReportServer is the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="0767e-126">*7*</span><span class="sxs-lookup"><span data-stu-id="0767e-126">*7*</span></span>|<span data-ttu-id="0767e-127">SQLBrowser は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser サービスです。</span><span class="sxs-lookup"><span data-stu-id="0767e-127">SQLBrowser is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0767e-128">参照</span><span class="sxs-lookup"><span data-stu-id="0767e-128">See Also</span></span>  
 <span data-ttu-id="0767e-129">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0767e-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
