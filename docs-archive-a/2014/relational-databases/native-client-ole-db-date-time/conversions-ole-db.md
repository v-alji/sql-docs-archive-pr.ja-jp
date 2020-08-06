---
title: バインドと変換 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
ms.assetid: c187df58-a8c8-4c74-a76f-663abbc5f0c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 95c73bdad80b5f948a45235ad208ab307fcceff3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644468"
---
# <a name="bindings-and-conversions-ole-db"></a><span data-ttu-id="12f44-102">バインドと変換 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="12f44-102">Bindings and Conversions (OLE DB)</span></span>
  <span data-ttu-id="12f44-103">ここでは、`datetime` 値と `datetimeoffset` 値との間で変換を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="12f44-103">This section discusses how to convert between `datetime` and `datetimeoffset` values.</span></span> <span data-ttu-id="12f44-104">ここで説明する変換は、OLE DB によって既に提供されているか、OLE DB の一貫性がある拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="12f44-104">The conversions described in this section are either already provided by OLE DB or are a consistent extension of OLE DB.</span></span>  
  
 <span data-ttu-id="12f44-105">OLE DB における日付と時刻のリテラルと文字列の形式は、通常 ISO に従うため、クライアントのロケールに依存しません。</span><span class="sxs-lookup"><span data-stu-id="12f44-105">The format of literals and strings for dates and times in OLE DB generally follows ISO, and is not dependent on the client locale.</span></span> <span data-ttu-id="12f44-106">これには、標準が OLE オートメーションである DBTYPE_DATE という例外があります。</span><span class="sxs-lookup"><span data-stu-id="12f44-106">One exception is DBTYPE_DATE, where the standard is OLE Automation.</span></span> <span data-ttu-id="12f44-107">ただし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client では、クライアントとの間でデータが転送される際に型の変換しか実行されないため、アプリケーションでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client に DBTYPE_DATE と文字列形式の変換を強制することができません。</span><span class="sxs-lookup"><span data-stu-id="12f44-107">However, because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client only converts between types when data is transmitted to or from the client, there is no way for an application to force [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client to convert between DBTYPE_DATE and string formats.</span></span> <span data-ttu-id="12f44-108">それ以外の場合、文字列では次の形式を使用します (角かっこに囲まれたテキストは省略可能な要素を示します)。</span><span class="sxs-lookup"><span data-stu-id="12f44-108">Otherwise, strings use the following formats (text in brackets indicates an optional element):</span></span>  
  
-   <span data-ttu-id="12f44-109">`datetime` 型の文字列と `datetimeoffset` 型の文字列の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12f44-109">The format of `datetime` and `datetimeoffset` strings is:</span></span>  
  
     <span data-ttu-id="12f44-110">*yyyy* -*mm* -*dd*[ *hh*:*mm*:*ss*[.*9999999*] [??</span><span class="sxs-lookup"><span data-stu-id="12f44-110">*yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ??</span></span> <span data-ttu-id="12f44-111">*hh*:*mm*]]</span><span class="sxs-lookup"><span data-stu-id="12f44-111">*hh*:*mm*]]</span></span>  
  
-   <span data-ttu-id="12f44-112">`time` 型の文字列の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12f44-112">The format of `time` strings is:</span></span>  
  
     <span data-ttu-id="12f44-113">*hh*:*mm*:*ss*[.*9999999*]</span><span class="sxs-lookup"><span data-stu-id="12f44-113">*hh*:*mm*:*ss*[.*9999999*]</span></span>  
  
-   <span data-ttu-id="12f44-114">`date` 型の文字列の形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12f44-114">The format of `date` strings is:</span></span>  
  
     <span data-ttu-id="12f44-115">*yyyy*-*mm*-*dd*</span><span class="sxs-lookup"><span data-stu-id="12f44-115">*yyyy*-*mm*-*dd*</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="12f44-116">以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client および SQLOLEDB では、標準の変換が失敗した場合に備えて OLE 変換が実装されていました。</span><span class="sxs-lookup"><span data-stu-id="12f44-116">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client and SQLOLEDB implemented OLE conversions, in case standard conversions failed.</span></span> <span data-ttu-id="12f44-117">このため、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 以降によって実行された変換には、OLE DB 仕様と異なるものがあります。</span><span class="sxs-lookup"><span data-stu-id="12f44-117">As a result, some conversions performed by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 and later differ from the OLE DB specification.</span></span>  
  
 <span data-ttu-id="12f44-118">文字列からの変換では、空白文字やフィールドの幅を柔軟に処理できます。</span><span class="sxs-lookup"><span data-stu-id="12f44-118">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="12f44-119">詳細については、「データ型のサポート」の「データ形式: 文字列とリテラル」を参照してください。 [OLE DB の日付と時刻の機能強化に関するセクションを](data-type-support-for-ole-db-date-and-time-improvements.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="12f44-119">For more information, see the "Data Formats: Strings and Literals" section in [Data Type Support for OLE DB Date and Time Improvements](data-type-support-for-ole-db-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="12f44-120">一般的な変換規則を次に示します。</span><span class="sxs-lookup"><span data-stu-id="12f44-120">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="12f44-121">文字列を日付型または時刻型に変換すると、文字列はまず ISO リテラルとして解析されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-121">When a string is converted to a date/time type, the string is first parsed as an ISO literal.</span></span> <span data-ttu-id="12f44-122">これが失敗すると、文字列は OLE 日付リテラルとして解析されます。OLE 日付リテラルには時刻要素があります。</span><span class="sxs-lookup"><span data-stu-id="12f44-122">If this fails, the string is parsed as an OLE date literal, which has time components.</span></span>  
  
-   <span data-ttu-id="12f44-123">時刻が存在しなくても受信側が時刻を格納できる場合、時刻は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-123">If no time is present but the receiver can store time, the time is set to zero.</span></span> <span data-ttu-id="12f44-124">日付が存在しなくても受信側が日付を格納できる場合、ISO 変換を使用すると日付は現在の日付に設定され、OLE 変換を使用すると日付は 1899-12-30 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-124">If no date is present but the receiver can store a date, the date is set to the current date when ISO conversions are used and to 1899-12-30 when OLE conversions are used.</span></span>  
  
-   <span data-ttu-id="12f44-125">クライアントが使用しているデータ型にタイム ゾーンが存在しなくても、サーバーがタイム ゾーンを格納できる場合、クライアントのデータはクライアントのタイム ゾーンで表されていると仮定されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-125">If no timezone is present in the data type that the client is using, but the server can store timezone, the data on the client is assumed to be in the client timezone.</span></span>  
  
-   <span data-ttu-id="12f44-126">サーバーにタイム ゾーンが存在しなくても、クライアントにタイム ゾーン情報がある場合、UTC のタイム ゾーンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-126">If no timezone is present at the server but the client has timezone information, the UTC timezone is assumed.</span></span> <span data-ttu-id="12f44-127">これはサーバーの動作とは異なります。</span><span class="sxs-lookup"><span data-stu-id="12f44-127">This differs from server behavior.</span></span>  
  
-   <span data-ttu-id="12f44-128">時刻が存在しても受信側が時刻を格納できない場合、時刻要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-128">If the time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="12f44-129">日付が存在しても受信側が日付を格納できない場合、日付要素は無視されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-129">If the date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="12f44-130">クライアントからサーバーへの変換時に秒または秒の小数部の切り捨てが発生すると、DB_E_ERRORSOCCURRED が返され、状態 DBSTATUS_E_DATAOVERFLOW が設定されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-130">If truncation of seconds or fractional seconds occurs when converting from client to server, DB_E_ERRORSOCCURRED is returned and the status DBSTATUS_E_DATAOVERFLOW is set.</span></span>  
  
-   <span data-ttu-id="12f44-131">サーバーからクライアントへの変換時に秒または秒の小数部の切り捨てが発生すると、DBSTATUS_S_TRUNCATED が設定されます。</span><span class="sxs-lookup"><span data-stu-id="12f44-131">If truncation of seconds or fractional seconds occurs when converting from server to client, DBSTATUS_S_TRUNCATED is set</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12f44-132">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="12f44-132">In This Section</span></span>  
 [<span data-ttu-id="12f44-133">クライアントからサーバーへの変換</span><span class="sxs-lookup"><span data-stu-id="12f44-133">Conversions Performed from Client to Server</span></span>](conversions-performed-from-client-to-server.md)  
 <span data-ttu-id="12f44-134">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB を使用して作成されたクライアント アプリケーションと [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) との間で実行される日付または時刻の変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="12f44-134">Describes date/time conversions performed between a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later).</span></span>  
  
 [<span data-ttu-id="12f44-135">サーバーからクライアントへの変換</span><span class="sxs-lookup"><span data-stu-id="12f44-135">Conversions Performed from Server to Client</span></span>](conversions-performed-from-server-to-client.md)  
 <span data-ttu-id="12f44-136">[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) と [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB を使用して作成されたクライアント アプリケーションとの間で実行される日付または時刻の変換について説明します。</span><span class="sxs-lookup"><span data-stu-id="12f44-136">Describes date/time conversions performed between [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (or later) and a client application written with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f44-137">参照</span><span class="sxs-lookup"><span data-stu-id="12f44-137">See Also</span></span>  
 [<span data-ttu-id="12f44-138">日付と時刻の強化機能 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="12f44-138">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
