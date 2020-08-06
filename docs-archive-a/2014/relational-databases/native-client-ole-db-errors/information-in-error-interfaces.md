---
title: エラー インターフェイス内の情報 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, errors
- IErrorRecords interface
- IErrorInfo interface
- OLE DB error handling, error interfaces
- ISQLErrorInfo interface
- errors [OLE DB], error interfaces
ms.assetid: 4620f03f-1193-43e7-ba19-ad022737d300
author: rothja
ms.author: jroth
ms.openlocfilehash: e9859ccbd804ba15685d84b98cbe74d4b096d98c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643806"
---
# <a name="information-in-error-interfaces"></a><span data-ttu-id="38a3f-102">エラー インターフェイス内の情報</span><span class="sxs-lookup"><span data-stu-id="38a3f-102">Information in Error Interfaces</span></span>
  <span data-ttu-id="38a3f-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、OLE DB 定義されたエラーインターフェイス**IErrorInfo**、 **Ierrorrecords**、 **ISQLErrorInfo**でエラーと状態に関する情報を報告します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider reports some error and status information in the OLE DB-defined error interfaces **IErrorInfo**, **IErrorRecords**, and **ISQLErrorInfo**.</span></span>  
  
 <span data-ttu-id="38a3f-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、次のように**IErrorInfo**メンバー関数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="38a3f-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **IErrorInfo** member functions as follows.</span></span>  
  
|<span data-ttu-id="38a3f-105">メンバー関数</span><span class="sxs-lookup"><span data-stu-id="38a3f-105">Member function</span></span>|<span data-ttu-id="38a3f-106">説明</span><span class="sxs-lookup"><span data-stu-id="38a3f-106">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="38a3f-107">**GetDescription**</span><span class="sxs-lookup"><span data-stu-id="38a3f-107">**GetDescription**</span></span>|<span data-ttu-id="38a3f-108">エラー メッセージを説明する文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-108">Descriptive error message string.</span></span>|  
|<span data-ttu-id="38a3f-109">**GetGUID**</span><span class="sxs-lookup"><span data-stu-id="38a3f-109">**GetGUID**</span></span>|<span data-ttu-id="38a3f-110">エラーを定義したインターフェイスの GUID を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-110">GUID of the interface that defined the error.</span></span>|  
|<span data-ttu-id="38a3f-111">**GetHelpContext**</span><span class="sxs-lookup"><span data-stu-id="38a3f-111">**GetHelpContext**</span></span>|<span data-ttu-id="38a3f-112">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="38a3f-112">Not supported.</span></span> <span data-ttu-id="38a3f-113">常にゼロが返されます。</span><span class="sxs-lookup"><span data-stu-id="38a3f-113">Always returns zero.</span></span>|  
|<span data-ttu-id="38a3f-114">**GetHelpFile**</span><span class="sxs-lookup"><span data-stu-id="38a3f-114">**GetHelpFile**</span></span>|<span data-ttu-id="38a3f-115">サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="38a3f-115">Not supported.</span></span> <span data-ttu-id="38a3f-116">常に NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="38a3f-116">Always returns NULL.</span></span>|  
|<span data-ttu-id="38a3f-117">**GetSource**</span><span class="sxs-lookup"><span data-stu-id="38a3f-117">**GetSource**</span></span>|<span data-ttu-id="38a3f-118">文字列 "Microsoft SQL Server Native Client" を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-118">String "Microsoft SQL Server Native Client".</span></span>|  
  
 <span data-ttu-id="38a3f-119">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、次のように、コンシューマーが使用できる**Ierrorrecords**メンバー関数をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="38a3f-119">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer-available **IErrorRecords** member functions as follows.</span></span>  
  
|<span data-ttu-id="38a3f-120">メンバー関数</span><span class="sxs-lookup"><span data-stu-id="38a3f-120">Member function</span></span>|<span data-ttu-id="38a3f-121">説明</span><span class="sxs-lookup"><span data-stu-id="38a3f-121">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="38a3f-122">**GetBasicErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="38a3f-122">**GetBasicErrorInfo**</span></span>|<span data-ttu-id="38a3f-123">エラーに関する基本情報を ERRORINFO 構造体に設定します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-123">Fills an ERRORINFO structure with basic information about an error.</span></span> <span data-ttu-id="38a3f-124">ERRORINFO 構造体には、エラーの HRESULT 戻り値およびエラーが適用されるプロバイダーとインターフェイスを特定するメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="38a3f-124">An ERRORINFO structure contains members that identify the HRESULT return value for the error, and the provider and interface to which the error applies.</span></span>|  
|<span data-ttu-id="38a3f-125">**GetCustomErrorObject**</span><span class="sxs-lookup"><span data-stu-id="38a3f-125">**GetCustomErrorObject**</span></span>|<span data-ttu-id="38a3f-126">**ISQLErrorInfo** インターフェイスと [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md) インターフェイスの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-126">Returns a reference on interfaces **ISQLErrorInfo,** and [ISQLServerErrorInfo](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md).</span></span>|  
|<span data-ttu-id="38a3f-127">**GetErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="38a3f-127">**GetErrorInfo**</span></span>|<span data-ttu-id="38a3f-128">**IErrorInfo** インターフェイスの参照を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-128">Returns a reference on an **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="38a3f-129">**GetErrorParameters**</span><span class="sxs-lookup"><span data-stu-id="38a3f-129">**GetErrorParameters**</span></span>|<span data-ttu-id="38a3f-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **GetErrorParameters**を介してコンシューマーにパラメーターを返しません。</span><span class="sxs-lookup"><span data-stu-id="38a3f-130">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not return parameters to the consumer through **GetErrorParameters**.</span></span>|  
|<span data-ttu-id="38a3f-131">**GetRecordCount**</span><span class="sxs-lookup"><span data-stu-id="38a3f-131">**GetRecordCount**</span></span>|<span data-ttu-id="38a3f-132">使用できるエラー レコードの数を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-132">Count of error records available.</span></span>|  
  
 <span data-ttu-id="38a3f-133">Native Client OLE DB プロバイダーでは、次のように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **ISQLErrorInfo:: GetSQLInfo**パラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="38a3f-133">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports **ISQLErrorInfo::GetSQLInfo** parameters as follows.</span></span>  
  
|<span data-ttu-id="38a3f-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38a3f-134">Parameter</span></span>|<span data-ttu-id="38a3f-135">説明</span><span class="sxs-lookup"><span data-stu-id="38a3f-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38a3f-136">*pbstrSQLState*</span><span class="sxs-lookup"><span data-stu-id="38a3f-136">*pbstrSQLState*</span></span>|<span data-ttu-id="38a3f-137">エラーの SQLSTATE 値を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-137">Returns a SQLSTATE value for the error.</span></span> <span data-ttu-id="38a3f-138">SQLSTATE 値は、SQL-92、ODBC と ISO SQL、および API の各仕様で定義されています。</span><span class="sxs-lookup"><span data-stu-id="38a3f-138">SQLSTATE values are defined in the SQL-92, ODBC and ISO SQL, and API specifications.</span></span> <span data-ttu-id="38a3f-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーのどちらも、実装固有の SQLSTATE 値を定義していません。</span><span class="sxs-lookup"><span data-stu-id="38a3f-139">Neither [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nor the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defined implementation-specific SQLSTATE values.</span></span>|  
|<span data-ttu-id="38a3f-140">*plNativeError*</span><span class="sxs-lookup"><span data-stu-id="38a3f-140">*plNativeError*</span></span>|<span data-ttu-id="38a3f-141">該当する場合は、**master.dbo.sysmessages** から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー番号を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-141">Returns the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error number from **master.dbo.sysmessages** when available.</span></span> <span data-ttu-id="38a3f-142">ネイティブクライアント OLE DB プロバイダーのデータソースを正常に初期化しようとすると、ネイティブエラーが発生し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="38a3f-142">Native errors are available after a successful attempt to initialize a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider data source.</span></span> <span data-ttu-id="38a3f-143">この試行の前に、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは常に0を返します。</span><span class="sxs-lookup"><span data-stu-id="38a3f-143">Prior to the attempt, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider always returns zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38a3f-144">参照</span><span class="sxs-lookup"><span data-stu-id="38a3f-144">See Also</span></span>  
 [<span data-ttu-id="38a3f-145">エラー</span><span class="sxs-lookup"><span data-stu-id="38a3f-145">Errors</span></span>](errors.md)  
  
  
