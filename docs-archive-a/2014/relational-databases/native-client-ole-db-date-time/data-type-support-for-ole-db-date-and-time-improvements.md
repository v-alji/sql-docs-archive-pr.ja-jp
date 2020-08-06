---
title: OLE DB の日付/時刻の強化に対するデータ型のサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], data type support
- OLE DB, date/time improvements
ms.assetid: d40e3fd6-9057-4371-8236-95cef300603e
author: rothja
ms.author: jroth
ms.openlocfilehash: 834583fdec63a8f613e623c239f9c3a1c9398950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738257"
---
# <a name="data-type-support-for-ole-db-date-and-time-improvements"></a><span data-ttu-id="aa510-102">OLE DB の日付/時刻の強化に対するデータ型のサポート</span><span class="sxs-lookup"><span data-stu-id="aa510-102">Data Type Support for OLE DB Date and Time Improvements</span></span>
  <span data-ttu-id="aa510-103">このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の日付および時刻データ型をサポートする OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa510-103">This topic provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date/time data types.</span></span>  
  
## <a name="data-type-mapping-in-rowsets-and-parameters"></a><span data-ttu-id="aa510-104">行セットとパラメーターでのデータ型マッピング</span><span class="sxs-lookup"><span data-stu-id="aa510-104">Data Type Mapping in Rowsets and Parameters</span></span>  
 <span data-ttu-id="aa510-105">OLE DB には、新しいサーバーの種類をサポートする 2 つの新しいデータ型 (DBTYPE_DBTIME2 と DBTYPE_DBTIMESTAMPOFFSET) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="aa510-105">OLE DB provides two new data types to support the new server types: DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="aa510-106">次の表に、完全なサーバーの型マッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="aa510-106">The following table shows the complete server type mapping:</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="aa510-107">のデータ型</span><span class="sxs-lookup"><span data-stu-id="aa510-107">data type</span></span>|<span data-ttu-id="aa510-108">OLE DB データ型</span><span class="sxs-lookup"><span data-stu-id="aa510-108">OLE DB data type</span></span>|<span data-ttu-id="aa510-109">値</span><span class="sxs-lookup"><span data-stu-id="aa510-109">Value</span></span>|  
|-----------------------------------------|----------------------|-----------|  
|<span data-ttu-id="aa510-110">DATETIME</span><span class="sxs-lookup"><span data-stu-id="aa510-110">datetime</span></span>|<span data-ttu-id="aa510-111">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="aa510-111">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="aa510-112">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="aa510-112">135 (oledb.h)</span></span>|  
|<span data-ttu-id="aa510-113">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="aa510-113">smalldatetime</span></span>|<span data-ttu-id="aa510-114">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="aa510-114">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="aa510-115">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="aa510-115">135 (oledb.h)</span></span>|  
|<span data-ttu-id="aa510-116">date</span><span class="sxs-lookup"><span data-stu-id="aa510-116">date</span></span>|<span data-ttu-id="aa510-117">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="aa510-117">DBTYPE_DBDATE</span></span>|<span data-ttu-id="aa510-118">133 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="aa510-118">133 (oledb.h)</span></span>|  
|<span data-ttu-id="aa510-119">time</span><span class="sxs-lookup"><span data-stu-id="aa510-119">time</span></span>|<span data-ttu-id="aa510-120">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="aa510-120">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="aa510-121">145 (sqlncli)</span><span class="sxs-lookup"><span data-stu-id="aa510-121">145 (sqlncli.h)</span></span>|  
|<span data-ttu-id="aa510-122">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="aa510-122">datetimeoffset</span></span>|<span data-ttu-id="aa510-123">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="aa510-123">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="aa510-124">146 (sqlncli)</span><span class="sxs-lookup"><span data-stu-id="aa510-124">146 (sqlncli.h)</span></span>|  
|<span data-ttu-id="aa510-125">datetime2</span><span class="sxs-lookup"><span data-stu-id="aa510-125">datetime2</span></span>|<span data-ttu-id="aa510-126">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="aa510-126">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="aa510-127">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="aa510-127">135 (oledb.h)</span></span>|  
  
## <a name="data-formats-strings-and-literals"></a><span data-ttu-id="aa510-128">データ形式 : 文字列とリテラル</span><span class="sxs-lookup"><span data-stu-id="aa510-128">Data Formats: Strings and Literals</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="aa510-129">のデータ型</span><span class="sxs-lookup"><span data-stu-id="aa510-129">data type</span></span>|<span data-ttu-id="aa510-130">OLE DB データ型</span><span class="sxs-lookup"><span data-stu-id="aa510-130">OLE DB data type</span></span>|<span data-ttu-id="aa510-131">クライアントで変換した場合の文字列の形式</span><span class="sxs-lookup"><span data-stu-id="aa510-131">String format for client conversions</span></span>|  
|-----------------------------------------|----------------------|------------------------------------------|  
|<span data-ttu-id="aa510-132">DATETIME</span><span class="sxs-lookup"><span data-stu-id="aa510-132">datetime</span></span>|<span data-ttu-id="aa510-133">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="aa510-133">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="aa510-134">'yyyy-mm-dd hh:mm:ss[.999]'</span><span class="sxs-lookup"><span data-stu-id="aa510-134">'yyyy-mm-dd hh:mm:ss[.999]'</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="aa510-135">では、datetime における秒の小数部の桁数を 3 桁までサポートします。</span><span class="sxs-lookup"><span data-stu-id="aa510-135">supports up to three fractional second digits for Datetime.</span></span>|  
|<span data-ttu-id="aa510-136">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="aa510-136">smalldatetime</span></span>|<span data-ttu-id="aa510-137">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="aa510-137">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="aa510-138">'yyyy-mm-dd hh:mm:ss'</span><span class="sxs-lookup"><span data-stu-id="aa510-138">'yyyy-mm-dd hh:mm:ss'</span></span><br /><br /> <span data-ttu-id="aa510-139">このデータ型の精度は 1 分です。</span><span class="sxs-lookup"><span data-stu-id="aa510-139">This data type has an accuracy of one minute.</span></span> <span data-ttu-id="aa510-140">秒の部分は、出力時には 0 になり、入力時にはサーバーによって丸められます。</span><span class="sxs-lookup"><span data-stu-id="aa510-140">The seconds component will be zero on output and will be rounded by the server on input.</span></span>|  
|<span data-ttu-id="aa510-141">date</span><span class="sxs-lookup"><span data-stu-id="aa510-141">date</span></span>|<span data-ttu-id="aa510-142">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="aa510-142">DBTYPE_DBDATE</span></span>|<span data-ttu-id="aa510-143">'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="aa510-143">'yyyy-mm-dd'</span></span>|  
|<span data-ttu-id="aa510-144">time</span><span class="sxs-lookup"><span data-stu-id="aa510-144">time</span></span>|<span data-ttu-id="aa510-145">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="aa510-145">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="aa510-146">'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="aa510-146">'hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="aa510-147">秒の小数部には、必要に応じて最大 7 桁まで指定できます。</span><span class="sxs-lookup"><span data-stu-id="aa510-147">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="aa510-148">datetime2</span><span class="sxs-lookup"><span data-stu-id="aa510-148">datetime2</span></span>|<span data-ttu-id="aa510-149">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="aa510-149">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="aa510-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span><span class="sxs-lookup"><span data-stu-id="aa510-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span></span><br /><br /> <span data-ttu-id="aa510-151">秒の小数部には、必要に応じて最大 7 桁まで指定できます。</span><span class="sxs-lookup"><span data-stu-id="aa510-151">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="aa510-152">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="aa510-152">datetimeoffset</span></span>|<span data-ttu-id="aa510-153">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="aa510-153">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="aa510-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span><span class="sxs-lookup"><span data-stu-id="aa510-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span></span><br /><br /> <span data-ttu-id="aa510-155">秒の小数部には、必要に応じて最大 7 桁まで指定できます。</span><span class="sxs-lookup"><span data-stu-id="aa510-155">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
  
 <span data-ttu-id="aa510-156">日付リテラルまたは時刻リテラルのエスケープ シーケンスに変更はありません。</span><span class="sxs-lookup"><span data-stu-id="aa510-156">There are no changes to the escape sequences for date/time literals.</span></span>  
  
 <span data-ttu-id="aa510-157">結果に含まれる秒の小数部にはコロン (:) ではなくドット (.) を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa510-157">Fractional seconds in results use a dot (.) rather than a colon (:).</span></span>  
  
 <span data-ttu-id="aa510-158">アプリケーションに返される文字列値は、指定された列に対して常に同じ長さになります。</span><span class="sxs-lookup"><span data-stu-id="aa510-158">String values returned to applications will always be the same length for a given column.</span></span> <span data-ttu-id="aa510-159">年、月、日、時、分、および秒の各部分は、最大幅に合わせて先頭にゼロが埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="aa510-159">Year, month, day, hour, minute, and second components will be padded with leading zeros to their maximum width.</span></span> <span data-ttu-id="aa510-160">日付と時間の間、および時間とタイムゾーン オフセットの間には空白が 1 つずつ入ります。</span><span class="sxs-lookup"><span data-stu-id="aa510-160">There will be exactly one space between date and time and exactly one space between the time and timezone offset.</span></span> <span data-ttu-id="aa510-161">タイム ゾーン オフセットの前には常に符号を指定します。</span><span class="sxs-lookup"><span data-stu-id="aa510-161">A timezone offset will always be preceded by a sign.</span></span> <span data-ttu-id="aa510-162">オフセットが 0 の場合は、正符号 (+) になります。</span><span class="sxs-lookup"><span data-stu-id="aa510-162">This sign will be a plus (+) when the offset is zero.</span></span> <span data-ttu-id="aa510-163">符号とオフセット値の間に空白はありません。</span><span class="sxs-lookup"><span data-stu-id="aa510-163">There will be no white space between the sign and the offset value.</span></span> <span data-ttu-id="aa510-164">秒の小数部では、必要に応じて、列に定義されている有効桁数になるまで後ろにゼロが埋め込まれますが、その有効桁数を超過することはありません。</span><span class="sxs-lookup"><span data-stu-id="aa510-164">Fractional seconds will be padded with trailing zeros, if necessary, up to the defined precision for the column, but no further.</span></span> <span data-ttu-id="aa510-165">datetime 列の場合、秒の小数部は 3 桁になります。</span><span class="sxs-lookup"><span data-stu-id="aa510-165">For datetime columns, there will be three fractional seconds digits.</span></span> <span data-ttu-id="aa510-166">smalldatetime 列の場合、秒の小数部がなく、秒は常にゼロになります。</span><span class="sxs-lookup"><span data-stu-id="aa510-166">For smalldatetime columns, there will be no fractional seconds digits and the seconds will always be zero.</span></span>  
  
 <span data-ttu-id="aa510-167">アプリケーションによって指定された文字列値を変換すると、柔軟性が向上し、各部分の値を最大幅より小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="aa510-167">Conversions from string values provided by the application will be more flexible and will allow component values less than maximum width.</span></span> <span data-ttu-id="aa510-168">年は 1 ～ 4 桁になります。</span><span class="sxs-lookup"><span data-stu-id="aa510-168">Years can be 1-4 digits.</span></span> <span data-ttu-id="aa510-169">月、日、時、分、および秒は 1 桁または 2 桁になります。</span><span class="sxs-lookup"><span data-stu-id="aa510-169">Months, days, hours, minutes, and seconds can be 1 or 2 digits.</span></span> <span data-ttu-id="aa510-170">日付と時刻の間および時刻とタイムゾーン オフセットの間には、任意の空白を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="aa510-170">There can be arbitrary white space between date/time and time/timezone offsets.</span></span> <span data-ttu-id="aa510-171">0 時 0 分のオフセットの符号は、正符号と負符号のどちらでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="aa510-171">The sign of an offset with zero hours and zero minutes can be plus or minus.</span></span> <span data-ttu-id="aa510-172">秒の小数部では、最大 9 桁になるように末尾にゼロを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="aa510-172">Trailing zeros are allowed for fractional seconds up to a maximum of 9 digits.</span></span> <span data-ttu-id="aa510-173">時刻部分は、小数点で終了して、秒の小数部を省略することができます。</span><span class="sxs-lookup"><span data-stu-id="aa510-173">A time component can terminate with a decimal point and no fractional seconds digits.</span></span>  
  
 <span data-ttu-id="aa510-174">空の文字列は、有効な日付リテラルまたは時間リテラルではありません。また、NULL 値を表すものでもありません。</span><span class="sxs-lookup"><span data-stu-id="aa510-174">An empty string is not a valid date/time literal and it does not represent a NULL value.</span></span> <span data-ttu-id="aa510-175">空の文字列を日付または時刻の値に変換しようとすると、SQLState 22018 のエラーが発生し、"キャストした文字コードが正しくありません" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="aa510-175">An attempt to convert an empty string to a date/time value will result in errors with SQLState 22018 and the message "Invalid character value for cast specification".</span></span>  
  
## <a name="data-formats-data-structures"></a><span data-ttu-id="aa510-176">データ形式 : データ構造体</span><span class="sxs-lookup"><span data-stu-id="aa510-176">Data Formats: Data Structures</span></span>  
 <span data-ttu-id="aa510-177">次に説明する OLE DB 固有の構造体では、OLE DB は ODBC と同じ制約に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="aa510-177">In the OLE DB-specific structures described below, OLE DB conforms to the same constraints as ODBC.</span></span> <span data-ttu-id="aa510-178">これらはグレゴリオ暦から取得されます。</span><span class="sxs-lookup"><span data-stu-id="aa510-178">These are taken from the Gregorian calendar:</span></span>  
  
-   <span data-ttu-id="aa510-179">月の範囲は 1 ～ 12 です。</span><span class="sxs-lookup"><span data-stu-id="aa510-179">Month range is 1 through 12.</span></span>  
  
-   <span data-ttu-id="aa510-180">日フィールドの範囲は 1 からその月の日数までです。この範囲は、うるう年を考慮して、年フィールドおよび月フィールドと一貫性を保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa510-180">Day field range is 1 through the number of days in the month, and must be consistent with year and month fields, taking account of leap years.</span></span>  
  
-   <span data-ttu-id="aa510-181">時刻の範囲は 0 ～ 23 です。</span><span class="sxs-lookup"><span data-stu-id="aa510-181">Hour range is 0 through 23.</span></span>  
  
-   <span data-ttu-id="aa510-182">分の範囲は 0 ～ 59 です。</span><span class="sxs-lookup"><span data-stu-id="aa510-182">Minute range is 0 through 59.</span></span>  
  
-   <span data-ttu-id="aa510-183">秒の範囲は 0 ～ 59 です。</span><span class="sxs-lookup"><span data-stu-id="aa510-183">Seconds range from 0 through 59.</span></span> <span data-ttu-id="aa510-184">この範囲では、恒星時との同期を維持するために最大 2 秒のうるう秒が許可されています。</span><span class="sxs-lookup"><span data-stu-id="aa510-184">This allows up to two leap seconds to maintain synchronization with sidereal time.</span></span>  
  
 <span data-ttu-id="aa510-185">次の既存の OLE DB 構造体の実装は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の新しい日付と時刻のデータ型をサポートするように変更されました。</span><span class="sxs-lookup"><span data-stu-id="aa510-185">Implementations for the following existing OLE DB structs have been modified to support the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span> <span data-ttu-id="aa510-186">ただし、定義は変更されていません。</span><span class="sxs-lookup"><span data-stu-id="aa510-186">The definitions, however, have not changed.</span></span>  
  
-   <span data-ttu-id="aa510-187">DBTYPE_DATE (オートメーション DATE 型です。</span><span class="sxs-lookup"><span data-stu-id="aa510-187">DBTYPE_DATE (This is an automation DATE type.</span></span> <span data-ttu-id="aa510-188">内部では `double` として表されます。</span><span class="sxs-lookup"><span data-stu-id="aa510-188">It is internally represented as a `double`..</span></span> <span data-ttu-id="aa510-189">整数部分は 1899 年 12 月 30 日からの日数で、小数部分は 1 日の端数になります。</span><span class="sxs-lookup"><span data-stu-id="aa510-189">The whole part is the number of days since December 30, 1899 and the fractional part is the fraction of a day.</span></span> <span data-ttu-id="aa510-190">この型の精度は 1 秒なので、有効な小数点以下桁数は 0 です。)</span><span class="sxs-lookup"><span data-stu-id="aa510-190">This type has an accuracy of 1 second, so has an effective scale of 0.)</span></span>  
  
-   <span data-ttu-id="aa510-191">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="aa510-191">DBTYPE_DBDATE</span></span>  
  
-   <span data-ttu-id="aa510-192">DBTYPE_DBTIME</span><span class="sxs-lookup"><span data-stu-id="aa510-192">DBTYPE_DBTIME</span></span>  
  
-   <span data-ttu-id="aa510-193">DBTYPE_DBTIMESTAMP (小数フィールドは、OLE DB で 10 億分の 1 秒 (ナノ秒) 単位の数値として定義され、範囲は 0 ～ 999,999,999 になります。)</span><span class="sxs-lookup"><span data-stu-id="aa510-193">DBTYPE_DBTIMESTAMP (the fraction field is defined by OLE DB as the number of billionths of a second (nanoseconds) and ranges from 0-999,999,999)</span></span>  
  
-   <span data-ttu-id="aa510-194">DBTYPE_FILETIME</span><span class="sxs-lookup"><span data-stu-id="aa510-194">DBTYPE_FILETIME</span></span>  
  
### <a name="dbtype_dbtime2"></a><span data-ttu-id="aa510-195">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="aa510-195">DBTYPE_DBTIME2</span></span>  
 <span data-ttu-id="aa510-196">この構造体では、32 ビットと 64 ビットの両方のオペレーティング システムで、12 バイトまで埋め込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="aa510-196">This struct is padded to 12 bytes on both 32-bit and 64-bit operating systems.</span></span>  
  
```  
typedef struct tagDBTIME2 {  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    } DBTIME2;  
```  
  
### <a name="dbtype_-dbtimestampoffset"></a><span data-ttu-id="aa510-197">DBTYPE_ DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="aa510-197">DBTYPE_ DBTIMESTAMPOFFSET</span></span>  
  
```  
typedef struct tagDBTIMESTAMPOFFSET {  
    SHORT year;  
    USHORT month;  
    USHORT day;  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    SHORT timezone_hour;  
    SHORT timezone_minute;  
    } DBTIMESTAMPOFFSET;  
```  
  
 <span data-ttu-id="aa510-198">`timezone_hour` が負の値の場合、`timezone_minute` は負の値または 0 である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa510-198">If `timezone_hour` is negative, `timezone_minute` must be negative or zero.</span></span> <span data-ttu-id="aa510-199">`timezone_hour` が正の値の場合、`timezone minute` は正の値または 0 である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa510-199">If `timezone_hour` is positive, `timezone minute` must be positive or zero.</span></span> <span data-ttu-id="aa510-200">`timezone_hour` が 0 の場合、`timezone minute` は -59 ～ +59 の値を保持できます。</span><span class="sxs-lookup"><span data-stu-id="aa510-200">If `timezone_hour` is zero, `timezone minute` can hold a value between -59 and +59.</span></span>  
  
### <a name="ssvariant"></a><span data-ttu-id="aa510-201">SSVARIANT</span><span class="sxs-lookup"><span data-stu-id="aa510-201">SSVARIANT</span></span>  
 <span data-ttu-id="aa510-202">この構造体は、新しい構造体 DBTYPE_DBTIME2 と DBTYPE_DBTIMESTAMPOFFSET を含み、適切な型に対しては秒の小数部の桁数が追加されています。</span><span class="sxs-lookup"><span data-stu-id="aa510-202">This struct now includes the new structures, DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET, and adds fractional seconds scale for appropriate types.</span></span>  
  
```  
struct SSVARIANT {  
   SSVARTYPE vt;  
   DWORD dwReserved1;  
   DWORD dwReserved2;  
   union {  
// ...  
      DBTIMESTAMP tsDateTimeVal;  
      DBDATE dDateVal;  
      struct _Time2Val {  
         DBTIME2 tTime2Val;  
         BYTE bScale;  
      } Time2Val;  
      struct _DateTimeVal {  
         DBTIMESTAMP tsDateTimeVal;  
         BYTE bScale;  
      } DateTimeVal;  
      struct _DateTimeOffsetVal {   
         DBTIMESTAMPOFFSET tsoDateTimeOffsetVal;  
         BYTE bScale;  
      } DateTimeOffsetVal;  
// ...  
   };  
};  
```  
  
 <span data-ttu-id="aa510-203">さらに、列挙の型を決定する、SSVARIANT の型のエンコーディングに関連付けられた列挙は、次のように拡張されます。</span><span class="sxs-lookup"><span data-stu-id="aa510-203">In addition, the enum associated with SSVARIANT type encoding, which determines the type of the enum, will be extended as follows:</span></span>  
  
```  
enum SQLVARENUM {  
// ...  
   // Datetime  
   VT_SS_DATETIME      = DBTYPE_DBTIMESTAMP,  
   VT_SS_SMALLDATETIME = 206,  
  
   VT_SS_DATE = DBTYPE_DBDATE,  
   VT_SS_TIME2 = DBTYPE_DBTIME2,  
   VT_SS_DATETIME2 = 212  
   VT_SS_DATETIMEOFFSET = DBTYPE_DBTIMESTAMPOFFSET  
};  
```  
  
 <span data-ttu-id="aa510-204">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Clien に移行中のアプリケーションが `sql_variant` を使用し、`datetime` の制限された有効桁数に依存しているとき、基になるスキーマが `datetime2` ではなく `datetime` を使用するように更新された場合は、この移行中のアプリケーションを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa510-204">Applications migrating to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client that use `sql_variant` and rely on the limited precision of `datetime` will have to be updated if the underlying schema is updated to use `datetime2` rather than `datetime`.</span></span>  
  
 <span data-ttu-id="aa510-205">また、SSVARIANT へのアクセス マクロが拡張され、次の部分が追加されました。</span><span class="sxs-lookup"><span data-stu-id="aa510-205">The access macros for SSVARIANT have also been extended with the addition of the following:</span></span>  
  
```  
#define V_SS_DATETIME2(X)       V_SS_UNION(X, DateTimeVal)  
#define V_SS_TIME2(X)           V_SS_UNION(X, Time2Val)  
#define V_SS_DATE(X)            V_SS_UNION(X, dDateVal)  
#define V_SS_DATETIMEOFFSET(X)  V_SS_UNION(X, DateTimeOffsetVal)  
```  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a><span data-ttu-id="aa510-206">ITableDefinition::CreateTable でのデータ型マッピング</span><span class="sxs-lookup"><span data-stu-id="aa510-206">Data Type Mapping in ITableDefinition::CreateTable</span></span>  
 <span data-ttu-id="aa510-207">次の型マッピングは、ITableDefinition::CreateTable で使用される DBCOLUMNDESC 構造体で使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa510-207">The following type mapping is used with DBCOLUMNDESC structures used by ITableDefinition::CreateTable:</span></span>  
  
|<span data-ttu-id="aa510-208">OLE DB データ型 (*wType*)</span><span class="sxs-lookup"><span data-stu-id="aa510-208">OLE DB data type (*wType*)</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="aa510-209">のデータ型</span><span class="sxs-lookup"><span data-stu-id="aa510-209">data type</span></span>|<span data-ttu-id="aa510-210">Notes</span><span class="sxs-lookup"><span data-stu-id="aa510-210">Notes</span></span>|  
|----------------------------------|-----------------------------------------|-----------|  
|<span data-ttu-id="aa510-211">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="aa510-211">DBTYPE_DBDATE</span></span>|<span data-ttu-id="aa510-212">date</span><span class="sxs-lookup"><span data-stu-id="aa510-212">date</span></span>||  
|<span data-ttu-id="aa510-213">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="aa510-213">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="aa510-214">`datetime2`(p)</span><span class="sxs-lookup"><span data-stu-id="aa510-214">`datetime2`(p)</span></span>|<span data-ttu-id="aa510-215">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、秒の小数部の有効桁数を決定するために、 *DBBFILE Desc bscale*メンバーを検査します。</span><span class="sxs-lookup"><span data-stu-id="aa510-215">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="aa510-216">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="aa510-216">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="aa510-217">`time`(p)</span><span class="sxs-lookup"><span data-stu-id="aa510-217">`time`(p)</span></span>|<span data-ttu-id="aa510-218">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、秒の小数部の有効桁数を決定するために、 *DBBFILE Desc bscale*メンバーを検査します。</span><span class="sxs-lookup"><span data-stu-id="aa510-218">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="aa510-219">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="aa510-219">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="aa510-220">`datetimeoffset`(p)</span><span class="sxs-lookup"><span data-stu-id="aa510-220">`datetimeoffset`(p)</span></span>|<span data-ttu-id="aa510-221">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、秒の小数部の有効桁数を決定するために、 *DBBFILE Desc bscale*メンバーを検査します。</span><span class="sxs-lookup"><span data-stu-id="aa510-221">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
  
 <span data-ttu-id="aa510-222">アプリケーションで*Wtype*の DBTYPE_DBTIMESTAMP を指定した場合、 `datetime2` *pwszTypeName*で型名を指定することによってへのマッピングをオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="aa510-222">When an application specifies DBTYPE_DBTIMESTAMP in *wType*, it can override the mapping to `datetime2` by supplying a type name in *pwszTypeName*.</span></span> <span data-ttu-id="aa510-223">`datetime`を指定する場合は、 *bscale*を3にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa510-223">If `datetime` is specified, *bScale* must be 3.</span></span> <span data-ttu-id="aa510-224">`smalldatetime`を指定する場合は、 *bscale*を0にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa510-224">If `smalldatetime` is specified, *bScale* must be 0.</span></span> <span data-ttu-id="aa510-225">*Bscale*が*Wtype*および*pwszTypeName*と一致しない場合、DB_E_BADSCALE が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa510-225">If *bScale* is not consistent with *wType* and *pwszTypeName*,DB_E_BADSCALE is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa510-226">参照</span><span class="sxs-lookup"><span data-stu-id="aa510-226">See Also</span></span>  
 [<span data-ttu-id="aa510-227">日付と時刻の強化機能 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="aa510-227">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
