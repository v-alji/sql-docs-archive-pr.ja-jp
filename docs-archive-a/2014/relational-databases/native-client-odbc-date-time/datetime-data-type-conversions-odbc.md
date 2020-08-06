---
title: datetime データ型変換 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- conversions [ODBC]
- bindings [ODBC]
- ODBC, bindings and conversions
ms.assetid: 66b9d282-c88d-40e5-93c2-fd5499a74458
author: rothja
ms.author: jroth
ms.openlocfilehash: 142e4388cb87055ddbc6faa7d5b1a92a627738c2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643295"
---
# <a name="datetime-data-type-conversions-odbc"></a><span data-ttu-id="27d8b-102">datetime データ型変換 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="27d8b-102">datetime Data Type Conversions (ODBC)</span></span>
  <span data-ttu-id="27d8b-103">次の変換は、ODBC によって既に定義されているか、ODBC の一貫性がある拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="27d8b-103">The following conversions are either already defined by ODBC or are a consistent extension of ODBC.</span></span> <span data-ttu-id="27d8b-104">各プロバイダーによって提供される変換は、プロバイダーが管理するコミュニティによって決まるので、プロバイダー間で一貫性がないことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="27d8b-104">The conversions supplied by each provider are determined by the community served by the provider, and there are often inconsistencies between providers as a result.</span></span> <span data-ttu-id="27d8b-105">角かっこで囲まれている値は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="27d8b-105">Values in square brackets are optional.</span></span>  
  
-   <span data-ttu-id="27d8b-106">datetime 型の文字列の形式は 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]' です。</span><span class="sxs-lookup"><span data-stu-id="27d8b-106">The format of datetime strings is 'yyyy-mm-dd[ hh:mm:ss[.9999999][ plus/minus hh:mm]]'</span></span>  
  
-   <span data-ttu-id="27d8b-107">time 型の文字列の形式は 'hh:mm:ss[.9999999]' です。</span><span class="sxs-lookup"><span data-stu-id="27d8b-107">The format of time strings is 'hh:mm:ss[.9999999]'</span></span>  
  
-   <span data-ttu-id="27d8b-108">date 型の文字列の形式は 'yyyy-mm-dd' です。</span><span class="sxs-lookup"><span data-stu-id="27d8b-108">The format of date strings is 'yyyy-mm-dd'</span></span>  
  
 <span data-ttu-id="27d8b-109">文字列からの変換では、空白文字やフィールドの幅を柔軟に処理できます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-109">Conversions from strings allow flexibility in white space and field width.</span></span> <span data-ttu-id="27d8b-110">詳細については、「 [ODBC の日付と時刻の機能強化のためのデータ型のサポート](data-type-support-for-odbc-date-and-time-improvements.md)」の「データ形式: 文字列とリテラル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27d8b-110">For more information, see the "Data Formats: Strings and Literals" section of [Data Type Support for ODBC Date and Time Improvements](data-type-support-for-odbc-date-and-time-improvements.md).</span></span>  
  
 <span data-ttu-id="27d8b-111">一般的な変換規則を次に示します。</span><span class="sxs-lookup"><span data-stu-id="27d8b-111">The following are general conversion rules:</span></span>  
  
-   <span data-ttu-id="27d8b-112">時刻が存在しなくても受信側が時刻を格納できる場合、時刻は 0 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-112">If no time is present but the receiver can store time, the time is set to zero.</span></span>  
  
-   <span data-ttu-id="27d8b-113">日付が存在しなくても受信側が日付を格納できる場合、現在の日付が使用されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-113">If no date is present but the receiver can store date, the current date is used.</span></span>  
  
-   <span data-ttu-id="27d8b-114">クライアントが使用しているデータ型にタイム ゾーンが存在しなくても、サーバーがタイム ゾーンを格納できる場合、日付はクライアントのタイム ゾーンで格納されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-114">If no timezone is present in the data type that the client is using but the server can store timezone, the date is stored in the client timezone.</span></span> <span data-ttu-id="27d8b-115">これはサーバーの動作とは異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="27d8b-115">Note that this differs from the server behavior.</span></span>  
  
-   <span data-ttu-id="27d8b-116">サーバーの型にタイム ゾーンが存在しなくても、クライアントの型にタイム ゾーンがある場合、時刻は UTC に変換されてからサーバーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-116">If no timezone is present in the server type but the client type has a timezone, time is converted to UTC before being stored on the server.</span></span>  
  
-   <span data-ttu-id="27d8b-117">時刻が存在するが、受信側が時刻を格納できない場合、時刻部分は無視されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-117">If time is present but the receiver cannot store time, the time component is ignored.</span></span>  
  
-   <span data-ttu-id="27d8b-118">日付が存在するが、受信側が日付を格納できない場合、日付部分は無視されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-118">If a date is present but the receiver cannot store the date, the date component is ignored.</span></span>  
  
-   <span data-ttu-id="27d8b-119">C データ型から SQL データ型に変換する際に秒または秒の小数部の切り捨てが発生すると、"Datetime フィールド オーバーフロー" というメッセージで SQLSTATE 22008 の診断レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-119">If truncation of seconds or fractional seconds occurs when converting from C to SQL, a diagnostic record is generated with SQLSTATE 22008 and the message "Datetime field overflow".</span></span>  
  
-   <span data-ttu-id="27d8b-120">SQL データ型から C データ型に変換する際に秒または秒の小数部の切り捨てが発生すると、"分数が切り捨てられました" というメッセージで SQLSTATE 01S07 の診断レコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="27d8b-120">If truncation of seconds or fractional seconds occurs when converting from SQL to C, a diagnostic record is generated with SQLSTATE 01S07 and the message "Fractional truncation".</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27d8b-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="27d8b-121">In This Section</span></span>  
 [<span data-ttu-id="27d8b-122">C から SQL への変換</span><span class="sxs-lookup"><span data-stu-id="27d8b-122">Conversions from C to SQL</span></span>](datetime-data-type-conversions-from-c-to-sql.md)  
 <span data-ttu-id="27d8b-123">C 型から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付型または時刻型に変換する際に考慮する問題を示します。</span><span class="sxs-lookup"><span data-stu-id="27d8b-123">Lists issues to consider when you convert from C types to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types.</span></span>  
  
 [<span data-ttu-id="27d8b-124">SQL から C への変換</span><span class="sxs-lookup"><span data-stu-id="27d8b-124">Conversions from SQL to C</span></span>](datetime-data-type-conversions-from-sql-to-c.md)  
 <span data-ttu-id="27d8b-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付型または時刻型から C 型に変換する際に考慮する問題を示します。</span><span class="sxs-lookup"><span data-stu-id="27d8b-125">Lists issues to consider when you convert from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data/time types to C types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d8b-126">参照</span><span class="sxs-lookup"><span data-stu-id="27d8b-126">See Also</span></span>  
 [<span data-ttu-id="27d8b-127">ODBC&#41;&#40;の日付と時刻の改善</span><span class="sxs-lookup"><span data-stu-id="27d8b-127">Date and Time Improvements &#40;ODBC&#41;</span></span>](date-and-time-improvements-odbc.md)  
  
  
