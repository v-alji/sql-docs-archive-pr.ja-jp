---
title: 日付と時刻の形式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- time data types [Integration Services]
- fast parse [Integration Services]
- date data types
- date and time formats for fast parse
ms.assetid: bed6e2c1-791a-4fa1-b29f-cbfdd1fa8d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e6c461c0cfed6a776875831a46c94c70d895ba3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633230"
---
# <a name="date-and-time-formats"></a><span data-ttu-id="48cb9-102">日付および時刻の形式</span><span class="sxs-lookup"><span data-stu-id="48cb9-102">Date and Time Formats</span></span>
  <span data-ttu-id="48cb9-103">高速解析は、データを解析するための高速で単純なルーチンのセットです。</span><span class="sxs-lookup"><span data-stu-id="48cb9-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="48cb9-104">高速解析では、日付および時刻のデータ型に対し次の形式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="48cb9-104">Fast parse supports the following formats for date and time data types.</span></span>  
  
## <a name="date-data-types"></a><span data-ttu-id="48cb9-105">日付データ型</span><span class="sxs-lookup"><span data-stu-id="48cb9-105">Date Data Types</span></span>  
 <span data-ttu-id="48cb9-106">高速解析では、次の文字列形式の日付データがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="48cb9-106">Fast parse supports the following string formats for date data:</span></span>  
  
-   <span data-ttu-id="48cb9-107">先頭の空白文字を含む日付の形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-107">Date formats that include leading white spaces.</span></span> <span data-ttu-id="48cb9-108">たとえば、値 " 2004- 02-03" は有効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-108">For example, the value " 2004- 02-03" is valid.</span></span>  
  
-   <span data-ttu-id="48cb9-109">次の表に示す ISO 8601 形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-109">ISO 8601 formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="48cb9-110">形式</span><span class="sxs-lookup"><span data-stu-id="48cb9-110">Format</span></span>|<span data-ttu-id="48cb9-111">説明</span><span class="sxs-lookup"><span data-stu-id="48cb9-111">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="48cb9-112">YYYYMMDD</span><span class="sxs-lookup"><span data-stu-id="48cb9-112">YYYYMMDD</span></span><br /><br /> <span data-ttu-id="48cb9-113">YYYY-MM-DD</span><span class="sxs-lookup"><span data-stu-id="48cb9-113">YYYY-MM-DD</span></span>|<span data-ttu-id="48cb9-114">4 桁の年、2 桁の月、および 2 桁の日を表す、基本および拡張形式です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-114">Basic and extended formats for a four-digit year, a two-digit month, and a two-digit day.</span></span> <span data-ttu-id="48cb9-115">拡張形式では、日付部分はハイフン (-) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-115">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="48cb9-116">YYYY-MM</span><span class="sxs-lookup"><span data-stu-id="48cb9-116">YYYY-MM</span></span>|<span data-ttu-id="48cb9-117">4 桁の年および 2 桁の月を表す、有効桁数を減らした基本および拡張形式です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-117">Basic and extended reduced precision formats for a four-digit year and a two-digit month.</span></span> <span data-ttu-id="48cb9-118">拡張形式では、日付部分はハイフン (-) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-118">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="48cb9-119">YYYY</span><span class="sxs-lookup"><span data-stu-id="48cb9-119">YYYY</span></span>|<span data-ttu-id="48cb9-120">4 桁の年を表す、有効桁数を減らした形式です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-120">Reduced precision format is a four-digit year.</span></span>|  
  
 <span data-ttu-id="48cb9-121">高速解析では、次の形式の日付データはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="48cb9-121">Fast parse does not support the following formats for date data:</span></span>  
  
-   <span data-ttu-id="48cb9-122">アルファベットの月の値。</span><span class="sxs-lookup"><span data-stu-id="48cb9-122">Alphabetical month values.</span></span> <span data-ttu-id="48cb9-123">たとえば、日付形式 Oct-31-2003 は無効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-123">For example, the date format Oct-31-2003 is not valid.</span></span>  
  
-   <span data-ttu-id="48cb9-124">DD-MM-YYYY や MM-DD-YYYY などのあいまいな形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-124">Ambiguous formats such as DD-MM-YYYY and MM-DD-YYYY.</span></span> <span data-ttu-id="48cb9-125">たとえば、03-04-1995 や 04-03-1995 の日付は無効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-125">For example, the dates 03-04-1995 and 04-03-1995 are not valid.</span></span>  
  
-   <span data-ttu-id="48cb9-126">4 桁の暦年と、その年の日付を 3 桁で表す、基本および拡張の切り捨て形式。たとえば YYYYDDD や YYYY-DDD は無効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-126">Basic and extended truncated formats for a four-digit calendar year and a three-digit day within a year, YYYYDDD and YYYY-DDD.</span></span>  
  
-   <span data-ttu-id="48cb9-127">4 桁の年、2 桁の週番号、および 1 桁の曜日番号を表す、基本および拡張の切り捨て形式。たとえば YYYYWwwD や YYYY-Www-D は無効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-127">Basic and extended formats for a four-digit year, a two-digit number for the week of the year, and a one-digit number for the day of the week, YYYYWwwD and YYYY-Www-D</span></span>  
  
-   <span data-ttu-id="48cb9-128">年と週を 4 桁の年と 2 桁の週番号で表す、基本および拡張の切り捨て形式。たとえば YYYWww や YYYY-Www は無効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-128">Basic and extended truncated formats for a year and week date are a four-digit year and a two-digit number for the week, YYYWww and YYYY-Www</span></span>  
  
 <span data-ttu-id="48cb9-129">高速解析では、DT_DBDATE としてデータを出力します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-129">Fast parse outputs the data as DT_DBDATE.</span></span> <span data-ttu-id="48cb9-130">切り捨て形式の日付の値は、埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-130">Date values in truncated formats are padded.</span></span> <span data-ttu-id="48cb9-131">たとえば、YYYY は YYYY0101 になります。</span><span class="sxs-lookup"><span data-stu-id="48cb9-131">For example, YYYY becomes YYYY0101.</span></span>  
  
 <span data-ttu-id="48cb9-132">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48cb9-132">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="time-data-type"></a><span data-ttu-id="48cb9-133">時刻データ型</span><span class="sxs-lookup"><span data-stu-id="48cb9-133">Time Data Type</span></span>  
 <span data-ttu-id="48cb9-134">高速解析では、次の文字列形式の時刻データがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="48cb9-134">Fast parse supports the following string formats for time data:</span></span>  
  
-   <span data-ttu-id="48cb9-135">先頭の空白文字を含む時刻の形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-135">Time formats that include leading white spaces.</span></span> <span data-ttu-id="48cb9-136">たとえば、値 " 10:24" は有効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-136">For example, the value " 10:24" is valid.</span></span>  
  
-   <span data-ttu-id="48cb9-137">24 時間形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-137">24-hour format.</span></span> <span data-ttu-id="48cb9-138">高速解析では、AM および PM の表記はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="48cb9-138">Fast parse does not support the AM and PM notation.</span></span>  
  
-   <span data-ttu-id="48cb9-139">次の表に示す ISO 8601 時刻形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-139">ISO 8601 time formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="48cb9-140">形式</span><span class="sxs-lookup"><span data-stu-id="48cb9-140">Format</span></span>|<span data-ttu-id="48cb9-141">説明</span><span class="sxs-lookup"><span data-stu-id="48cb9-141">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="48cb9-142">HHMISS</span><span class="sxs-lookup"><span data-stu-id="48cb9-142">HHMISS</span></span><br /><br /> <span data-ttu-id="48cb9-143">HH:MI:SS</span><span class="sxs-lookup"><span data-stu-id="48cb9-143">HH:MI:SS</span></span>|<span data-ttu-id="48cb9-144">2 桁の時、2 桁の分、および 2 桁の秒を表す、基本および拡張形式です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-144">Basic and extended formats for a two-digit hour, a two-digit minute, and a two-digit second.</span></span> <span data-ttu-id="48cb9-145">拡張形式では、時刻の部分はコロン (:) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-145">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="48cb9-146">HHMI</span><span class="sxs-lookup"><span data-stu-id="48cb9-146">HHMI</span></span><br /><br /> <span data-ttu-id="48cb9-147">HH:MI</span><span class="sxs-lookup"><span data-stu-id="48cb9-147">HH:MI</span></span>|<span data-ttu-id="48cb9-148">2 桁の時と 2 桁の分を表す、基本および拡張の切り捨て形式です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-148">Basic and extended truncated format for a two-digit hour and a two-digit minute.</span></span> <span data-ttu-id="48cb9-149">拡張形式では、時刻の部分はコロン (:) で区切られます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-149">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="48cb9-150">HH</span><span class="sxs-lookup"><span data-stu-id="48cb9-150">HH</span></span>|<span data-ttu-id="48cb9-151">2 桁の時を表す切り捨て形式です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-151">Truncated format for a two-digit hour.</span></span>|  
    |<span data-ttu-id="48cb9-152">00:00:00</span><span class="sxs-lookup"><span data-stu-id="48cb9-152">00:00:00</span></span><br /><br /> <span data-ttu-id="48cb9-153">000000</span><span class="sxs-lookup"><span data-stu-id="48cb9-153">000000</span></span><br /><br /> <span data-ttu-id="48cb9-154">0000</span><span class="sxs-lookup"><span data-stu-id="48cb9-154">0000</span></span><br /><br /> <span data-ttu-id="48cb9-155">00</span><span class="sxs-lookup"><span data-stu-id="48cb9-155">00</span></span><br /><br /> <span data-ttu-id="48cb9-156">240000</span><span class="sxs-lookup"><span data-stu-id="48cb9-156">240000</span></span><br /><br /> <span data-ttu-id="48cb9-157">24:00:00</span><span class="sxs-lookup"><span data-stu-id="48cb9-157">24:00:00</span></span><br /><br /> <span data-ttu-id="48cb9-158">2400</span><span class="sxs-lookup"><span data-stu-id="48cb9-158">2400</span></span><br /><br /> <span data-ttu-id="48cb9-159">24</span><span class="sxs-lookup"><span data-stu-id="48cb9-159">24</span></span>|<span data-ttu-id="48cb9-160">午前 0 時を表す形式です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-160">The format for midnight.</span></span>|  
  
-   <span data-ttu-id="48cb9-161">次の表に示す、タイム ゾーンを指定する時刻形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-161">Time formats that specify a time zone, as listed in the following table:.</span></span>  
  
    |<span data-ttu-id="48cb9-162">形式</span><span class="sxs-lookup"><span data-stu-id="48cb9-162">Format</span></span>|<span data-ttu-id="48cb9-163">説明</span><span class="sxs-lookup"><span data-stu-id="48cb9-163">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="48cb9-164">+HH:MI</span><span class="sxs-lookup"><span data-stu-id="48cb9-164">+HH:MI</span></span><br /><br /> <span data-ttu-id="48cb9-165">+HHMI</span><span class="sxs-lookup"><span data-stu-id="48cb9-165">+HHMI</span></span>|<span data-ttu-id="48cb9-166">ローカル時間を求めるために協定世界時 (UTC) に加算される時間数と分数を示す基本形式と拡張形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-166">Basic and extended formats that indicate the number of hours and minutes that are added to Coordinated Universal Time (UTC) to obtain the local time.</span></span>|  
    |<span data-ttu-id="48cb9-167">-HH:MI</span><span class="sxs-lookup"><span data-stu-id="48cb9-167">-HH:MI</span></span><br /><br /> <span data-ttu-id="48cb9-168">-HHMI</span><span class="sxs-lookup"><span data-stu-id="48cb9-168">-HHMI</span></span>|<span data-ttu-id="48cb9-169">ローカル時間を求めるために協定世界時 (UTC) から減算される時間数と分数を示す基本形式と拡張形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-169">Basic and extended formats that indicate the number of hours and minutes that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="48cb9-170">+HH</span><span class="sxs-lookup"><span data-stu-id="48cb9-170">+HH</span></span>|<span data-ttu-id="48cb9-171">ローカル時間を求めるために UTC に加算される時間数を示す切り捨て形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-171">Truncated format that indicates the number of hours that are added to UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="48cb9-172">-HH</span><span class="sxs-lookup"><span data-stu-id="48cb9-172">-HH</span></span>|<span data-ttu-id="48cb9-173">ローカル時間を求めるために UTC から減算される時間数を示す切り捨て形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-173">Truncated format that indicates the number of hours that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="48cb9-174">Z</span><span class="sxs-lookup"><span data-stu-id="48cb9-174">Z</span></span>|<span data-ttu-id="48cb9-175">時間が UTC で表されていることを示す 0 の値。</span><span class="sxs-lookup"><span data-stu-id="48cb9-175">A value of 0 that indicates the time is represented in UTC.</span></span>|  
  
     <span data-ttu-id="48cb9-176">タイム ゾーン要素を含むことのできるすべての時刻および日付/時刻データの形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-176">The formats for all time and date/time data can include a time zone element.</span></span> <span data-ttu-id="48cb9-177">ただし、データが DT_DBTIMESTAMPOFFSET 型以外の場合、タイム ゾーン値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-177">However, the system ignores the time zone value except when the data is of type DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="48cb9-178">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48cb9-178">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
     <span data-ttu-id="48cb9-179">タイム ゾーン要素を含む形式では、次の例に示すように、時間要素とタイム ゾーン要素の間にスペースはありません。</span><span class="sxs-lookup"><span data-stu-id="48cb9-179">In formats that include a time zone element, there is no space between the time element and the time zone element, as shown in the following example:</span></span>  
  
     <span data-ttu-id="48cb9-180">HH:MI:SS[+HH:MI]</span><span class="sxs-lookup"><span data-stu-id="48cb9-180">HH:MI:SS[+HH:MI]</span></span>  
  
     <span data-ttu-id="48cb9-181">上の例の角かっこは、タイム ゾーン値が省略可能であることを示します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-181">The brackets in the previous example indicate that the time zone value is optional.</span></span>  
  
-   <span data-ttu-id="48cb9-182">次の表に示す、小数部を含む時刻形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-182">Time formats that include a decimal fraction, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="48cb9-183">形式</span><span class="sxs-lookup"><span data-stu-id="48cb9-183">Format</span></span>|<span data-ttu-id="48cb9-184">説明</span><span class="sxs-lookup"><span data-stu-id="48cb9-184">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="48cb9-185">HH[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="48cb9-185">HH[.nnnnnnn]</span></span>|<span data-ttu-id="48cb9-186">n は、時間の端数を表す 0 ～ 9999999 の範囲の値です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-186">n is a value between 0 and 9999999 that represents a fraction of hours.</span></span> <span data-ttu-id="48cb9-187">角かっこは、この値が省略可能であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="48cb9-187">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="48cb9-188">たとえば、値 12.750 は 12:45 を示します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-188">For example, the value 12.750 indicates 12:45.</span></span>|  
    |<span data-ttu-id="48cb9-189">HHMI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="48cb9-189">HHMI[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="48cb9-190">HH:MI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="48cb9-190">HH:MI[.nnnnnnn]</span></span>|<span data-ttu-id="48cb9-191">n は、分の端数を表す 0 ～ 9999999 の範囲の値です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-191">n is a value between 0 and 9999999 that represents a fraction of minutes.</span></span> <span data-ttu-id="48cb9-192">角かっこは、この値が省略可能であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="48cb9-192">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="48cb9-193">たとえば、値 1220.500 は 12:20:30 を示します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-193">For example, the value 1220.500 indicates 12:20:30.</span></span>|  
    |<span data-ttu-id="48cb9-194">HHMISS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="48cb9-194">HHMISS[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="48cb9-195">HH:MI:SS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="48cb9-195">HH:MI:SS[.nnnnnnn]</span></span>|<span data-ttu-id="48cb9-196">n は、秒の端数を表す 0 ～ 9999999 の範囲の値です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-196">n is a value between 0 and 9999999 that represents a fraction of seconds.</span></span> <span data-ttu-id="48cb9-197">角かっこは、この値が省略可能であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="48cb9-197">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="48cb9-198">たとえば、値 122040.250 は 12:20:40.15 を示します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-198">For example, the value 122040.250 indicates 12:20:40.15.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="48cb9-199">前の表の時刻形式の区切り文字には、小数点またはコンマを使用できます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-199">The fraction separator for the time formats in the previous table can be a decimal or a comma.</span></span>  
  
-   <span data-ttu-id="48cb9-200">次の例に示す、うるう秒を含む時刻値。</span><span class="sxs-lookup"><span data-stu-id="48cb9-200">Time values that include a leap second, as shown in the following examples:</span></span>  
  
     <span data-ttu-id="48cb9-201">23:59:60[.0000000]</span><span class="sxs-lookup"><span data-stu-id="48cb9-201">23:59:60[.0000000]</span></span>  
  
     <span data-ttu-id="48cb9-202">235960[.0000000]</span><span class="sxs-lookup"><span data-stu-id="48cb9-202">235960[.0000000]</span></span>  
  
 <span data-ttu-id="48cb9-203">高速解析では、DT_DBTIME および DT_DBTIME2 として文字列を出力します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-203">Fast parse outputs the strings as DT_DBTIME and DT_DBTIME2.</span></span> <span data-ttu-id="48cb9-204">切り捨て形式の時刻値は、埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-204">Time values in truncated formats are padded.</span></span> <span data-ttu-id="48cb9-205">たとえば、HH:MI は HH:MM:00.000 になります。</span><span class="sxs-lookup"><span data-stu-id="48cb9-205">For example, HH:MI becomes HH:MM:00.000.</span></span>  
  
 <span data-ttu-id="48cb9-206">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48cb9-206">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="datetime-data-type"></a><span data-ttu-id="48cb9-207">日付/時刻データ型</span><span class="sxs-lookup"><span data-stu-id="48cb9-207">Date/Time Data Type</span></span>  
 <span data-ttu-id="48cb9-208">高速解析では、次の文字列形式の日付/時刻データがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="48cb9-208">Fast parse supports the following string formats for date/time data:</span></span>  
  
-   <span data-ttu-id="48cb9-209">先頭の空白文字を含む形式。</span><span class="sxs-lookup"><span data-stu-id="48cb9-209">Formats that include leading white spaces.</span></span> <span data-ttu-id="48cb9-210">たとえば、値 "  2003-01-10T203910" は有効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-210">For example, the value "  2003-01-10T203910" is valid.</span></span>  
  
-   <span data-ttu-id="48cb9-211">YYYYMMDDT[HHMISS][+HH:MI] などの、大文字 T で区切られた有効な日付形式と有効な時刻形式、および有効なタイム ゾーン形式の組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="48cb9-211">Combinations of valid date formats and valid time formats separated by an uppercase T, and valid time zone formats, such as YYYYMMDDT[HHMISS][+HH:MI].</span></span> <span data-ttu-id="48cb9-212">時刻とタイム ゾーンの値は必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="48cb9-212">The time and time zone values are not required.</span></span> <span data-ttu-id="48cb9-213">たとえば、"2003-10-14" は有効です。</span><span class="sxs-lookup"><span data-stu-id="48cb9-213">For example, "2003-10-14" is valid.</span></span>  
  
 <span data-ttu-id="48cb9-214">高速解析では、期間はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="48cb9-214">Fast parse does not support time intervals.</span></span> <span data-ttu-id="48cb9-215">たとえば、YYYYMMDDThhmmss/YYYYMMDDThhmmss の形式の、開始および終了の日付と時刻で識別される期間は、解析できません。</span><span class="sxs-lookup"><span data-stu-id="48cb9-215">For example, a time interval identified by a start and end date and time in the format YYYYMMDDThhmmss/YYYYMMDDThhmmss cannot be parsed.</span></span>  
  
 <span data-ttu-id="48cb9-216">高速解析では、DT_DATE、DT_DBTIMESTAMP、DT_DBTIMESTAMP2、および DT_DBTIMESTAMPOFFSET として文字列を出力します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-216">Fast parse outputs the strings as DT_DATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="48cb9-217">切り捨て形式の日付/時刻値は、埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-217">Date/time values in truncated formats are padded.</span></span> <span data-ttu-id="48cb9-218">次の表に、欠けている日付および時刻の部分に対して追加される値を示します。</span><span class="sxs-lookup"><span data-stu-id="48cb9-218">The following table lists the values that are added for missing date and time parts.</span></span>  
  
|<span data-ttu-id="48cb9-219">日付/時刻部分</span><span class="sxs-lookup"><span data-stu-id="48cb9-219">Date/Time part</span></span>|<span data-ttu-id="48cb9-220">パディング</span><span class="sxs-lookup"><span data-stu-id="48cb9-220">Padding</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="48cb9-221">Seconds</span><span class="sxs-lookup"><span data-stu-id="48cb9-221">Seconds</span></span>|<span data-ttu-id="48cb9-222">00 が追加されます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-222">Add 00.</span></span>|  
|<span data-ttu-id="48cb9-223">分</span><span class="sxs-lookup"><span data-stu-id="48cb9-223">Minutes</span></span>|<span data-ttu-id="48cb9-224">00:00 が追加されます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-224">Add 00:00.</span></span>|  
|<span data-ttu-id="48cb9-225">時間</span><span class="sxs-lookup"><span data-stu-id="48cb9-225">Hour</span></span>|<span data-ttu-id="48cb9-226">00:00:00 が追加されます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-226">Add 00:00:00.</span></span>|  
|<span data-ttu-id="48cb9-227">日間</span><span class="sxs-lookup"><span data-stu-id="48cb9-227">Day</span></span>|<span data-ttu-id="48cb9-228">月の日付として 01 が追加されます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-228">Add 01 for the day of the month.</span></span>|  
|<span data-ttu-id="48cb9-229">Month</span><span class="sxs-lookup"><span data-stu-id="48cb9-229">Month</span></span>|<span data-ttu-id="48cb9-230">年の月として 01 が追加されます。</span><span class="sxs-lookup"><span data-stu-id="48cb9-230">Add 01 for the month of the year.</span></span>|  
  
 <span data-ttu-id="48cb9-231">詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48cb9-231">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
  
