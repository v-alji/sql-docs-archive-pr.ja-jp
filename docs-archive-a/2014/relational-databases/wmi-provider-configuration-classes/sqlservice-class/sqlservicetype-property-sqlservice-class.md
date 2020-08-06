---
title: SqlServiceType プロパティ (Sqlservicetype クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SqlServiceType Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SqlServiceType property
ms.assetid: dbff2968-3011-41d6-a141-52d814af0213
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 18e0fc741d19eefbb93dbcb7fb6fd4a221ce86d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87717624"
---
# <a name="sqlservicetype-property-sqlservice-class"></a><span data-ttu-id="d6220-102">SqlServiceType プロパティ (SqlService クラス)</span><span class="sxs-lookup"><span data-stu-id="d6220-102">SqlServiceType Property (SqlService Class)</span></span>
  <span data-ttu-id="d6220-103">マネージド サービスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="d6220-103">Gets the type of the managed service.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6220-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6220-104">Syntax</span></span>  
  
```  
  
object  
.SqlServiceType [= value]  
```  
  
## <a name="parts"></a><span data-ttu-id="d6220-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="d6220-105">Parts</span></span>  
 <span data-ttu-id="d6220-106">*object*</span><span class="sxs-lookup"><span data-stu-id="d6220-106">*object*</span></span>  
 <span data-ttu-id="d6220-107">サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d6220-107">A [SqlService Class](sqlservice-class.md) object that represents the service.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="d6220-108">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="d6220-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="d6220-109">サービスの種類を指定する uint32 値 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d6220-109">A uint32 value that specifies the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6220-110">解説</span><span class="sxs-lookup"><span data-stu-id="d6220-110">Remarks</span></span>  
 <span data-ttu-id="d6220-111">戻り値は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="d6220-111">Return values can be one of the following:</span></span>  
  
|<span data-ttu-id="d6220-112">Type</span><span class="sxs-lookup"><span data-stu-id="d6220-112">Type</span></span>|<span data-ttu-id="d6220-113">定義</span><span class="sxs-lookup"><span data-stu-id="d6220-113">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="d6220-114">*1*</span><span class="sxs-lookup"><span data-stu-id="d6220-114">*1*</span></span>|<span data-ttu-id="d6220-115">MSSQLSERVER は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="d6220-115">MSSQLSERVER is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="d6220-116">*2*</span><span class="sxs-lookup"><span data-stu-id="d6220-116">*2*</span></span>|<span data-ttu-id="d6220-117">SQLSERVERAGENT は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エージェント サービスです。</span><span class="sxs-lookup"><span data-stu-id="d6220-117">SQLSERVERAGENT is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent service.</span></span>|  
|<span data-ttu-id="d6220-118">*3*</span><span class="sxs-lookup"><span data-stu-id="d6220-118">*3*</span></span>|<span data-ttu-id="d6220-119">MSFTESQL は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] フルテキスト検索エンジン サービスです。</span><span class="sxs-lookup"><span data-stu-id="d6220-119">MSFTESQL is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Full-text Search Engine service.</span></span>|  
|<span data-ttu-id="d6220-120">*4*</span><span class="sxs-lookup"><span data-stu-id="d6220-120">*4*</span></span>|<span data-ttu-id="d6220-121">MsDtsServer は [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="d6220-121">MsDtsServer is the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="d6220-122">*5*</span><span class="sxs-lookup"><span data-stu-id="d6220-122">*5*</span></span>|<span data-ttu-id="d6220-123">MSSQLServerOLAPService は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="d6220-123">MSSQLServerOLAPService is the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="d6220-124">*6*</span><span class="sxs-lookup"><span data-stu-id="d6220-124">*6*</span></span>|<span data-ttu-id="d6220-125">ReportServer は [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="d6220-125">ReportServer is the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="d6220-126">*7*</span><span class="sxs-lookup"><span data-stu-id="d6220-126">*7*</span></span>|<span data-ttu-id="d6220-127">SQLBrowser は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser サービスです。</span><span class="sxs-lookup"><span data-stu-id="d6220-127">SQLBrowser is the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Browser service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6220-128">参照</span><span class="sxs-lookup"><span data-stu-id="d6220-128">See Also</span></span>  
 <span data-ttu-id="d6220-129">[サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="d6220-129">[Starting and Stopping Services](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)</span></span>  
  
  
