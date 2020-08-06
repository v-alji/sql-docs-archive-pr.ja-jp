---
title: 以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- earlier versions [SQL Server], import and export data formats
- -V switch
- data formats [SQL Server], earlier versions
- previous versions [SQL Server], import and export data formats
ms.assetid: e644696f-9017-428e-a5b3-d445d1c630b3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 274c984d6ecec8af8f5bea27496450a45fc2f1df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643339"
---
# <a name="import-native-and-character-format-data-from-earlier-versions-of-sql-server"></a><span data-ttu-id="eeea7-102">以前のバージョンの SQL Server からのネイティブ形式データおよび文字形式データのインポート</span><span class="sxs-lookup"><span data-stu-id="eeea7-102">Import Native and Character Format Data from Earlier Versions of SQL Server</span></span>
  <span data-ttu-id="eeea7-103">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]では、 **bcp** を使用すると、 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] からネイティブ形式データおよび文字形式データを **-V** スイッチを指定してインポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="eeea7-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], you can use **bcp** to import native and character format data from [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] by using the **-V** switch.</span></span> <span data-ttu-id="eeea7-104">**-V** スイッチを使用すると、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は指定された以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のデータ型を使用し、データ ファイル形式はその以前のバージョンのものと同じになります。</span><span class="sxs-lookup"><span data-stu-id="eeea7-104">The **-V** switch causes [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] to use data types from the specified earlier version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and the data file format are the same as the format in that earlier version.</span></span>  
  
 <span data-ttu-id="eeea7-105">データ ファイルに以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンを指定するには、 **-V** スイッチと次のいずれかの修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="eeea7-105">To specify an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version for a data file, use the **-V** switch with one of the following qualifiers:</span></span>  
  
|<span data-ttu-id="eeea7-106">SQL Server のバージョン</span><span class="sxs-lookup"><span data-stu-id="eeea7-106">SQL Server version</span></span>|<span data-ttu-id="eeea7-107">Qualifier</span><span class="sxs-lookup"><span data-stu-id="eeea7-107">Qualifier</span></span>|  
|------------------------|---------------|  
|[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]|<span data-ttu-id="eeea7-108">**-V80**</span><span class="sxs-lookup"><span data-stu-id="eeea7-108">**-V80**</span></span>|  
|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|<span data-ttu-id="eeea7-109">**-V90**</span><span class="sxs-lookup"><span data-stu-id="eeea7-109">**-V90**</span></span>|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|<span data-ttu-id="eeea7-110">**-V100**</span><span class="sxs-lookup"><span data-stu-id="eeea7-110">**-V100**</span></span>|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|<span data-ttu-id="eeea7-111">**-V 110**</span><span class="sxs-lookup"><span data-stu-id="eeea7-111">**-V 110**</span></span>|  
  
## <a name="interpretation-of-data-types"></a><span data-ttu-id="eeea7-112">データ型について</span><span class="sxs-lookup"><span data-stu-id="eeea7-112">Interpretation of Data Types</span></span>  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] <span data-ttu-id="eeea7-113">以降のバージョンでは、いくつかの新しいデータ型がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="eeea7-113">and later versions have support for some new types.</span></span> <span data-ttu-id="eeea7-114">以前の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バージョンに新しいデータ型をインポートする場合は、古い **bcp** クライアントで読み取ることが可能な形式でそのデータ型を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eeea7-114">When you want to import a new data type into an earlier [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version, the data type must be stored in a format that readable by the older **bcp** clients.</span></span> <span data-ttu-id="eeea7-115">次の表では、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]との互換性を維持するために、新しいデータ型がどのように変換されるかをまとめています。</span><span class="sxs-lookup"><span data-stu-id="eeea7-115">The following table summarizes how the new data types are converted for compatibility with the earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="eeea7-116">SQL Server 2005 の新しいデータ型</span><span class="sxs-lookup"><span data-stu-id="eeea7-116">New data types in SQL Server 2005</span></span>|<span data-ttu-id="eeea7-117">バージョン 6*x*の互換性のあるデータ型</span><span class="sxs-lookup"><span data-stu-id="eeea7-117">Compatible data types in version 6*x*</span></span>|<span data-ttu-id="eeea7-118">バージョン 70 の互換性のあるデータ型</span><span class="sxs-lookup"><span data-stu-id="eeea7-118">Compatible data types in version 70</span></span>|<span data-ttu-id="eeea7-119">バージョン 80 の互換性のあるデータ型</span><span class="sxs-lookup"><span data-stu-id="eeea7-119">Compatible data types in version 80</span></span>|  
|---------------------------------------|-------------------------------------------|-----------------------------------------|-----------------------------------------|  
|`bigint`|`decimal`|`decimal`|*|  
|`sql_variant`|`text`|`nvarchar(4000)`|*|  
|`varchar(max)`|`text`|`text`|`text`|  
|`nvarchar(max)`|`ntext`|`ntext`|`ntext`|  
|`varbinary(max)`|`image`|`image`|`image`|  
|<span data-ttu-id="eeea7-120">XML</span><span class="sxs-lookup"><span data-stu-id="eeea7-120">XML</span></span>|`ntext`|`ntext`|`ntext`|  
|<span data-ttu-id="eeea7-121">UDT<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="eeea7-121">UDT<sup>1</sup></span></span>|`image`|`image`|`image`|  
  
 <span data-ttu-id="eeea7-122">\*この型はネイティブでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="eeea7-122">\* This type is natively supported.</span></span>  
  
 <span data-ttu-id="eeea7-123"><sup>1</sup> UDT は、ユーザー定義型を示します。</span><span class="sxs-lookup"><span data-stu-id="eeea7-123"><sup>1</sup> UDT indicates a user defined type.</span></span>  
  
## <a name="exporting-using--v-80"></a><span data-ttu-id="eeea7-124">-V 80 を使用したエクスポート</span><span class="sxs-lookup"><span data-stu-id="eeea7-124">Exporting using -V 80</span></span>  
 <span data-ttu-id="eeea7-125">**-V80**スイッチを使用してデータを一括エクスポートする場合、、、 `nvarchar(max)` `varchar(max)` `varbinary(max)` 、XML、およびネイティブモードの UDT データは、、、およびデータのように4バイトのプレフィックスを使用して格納され `text` `image` `ntext` ます。これは、以降のバージョンの既定の8バイトのプレフィックス [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではなく、、、などです。</span><span class="sxs-lookup"><span data-stu-id="eeea7-125">When you bulk export data by using the **-V80** switch, `nvarchar(max)`, `varchar(max)`, `varbinary(max)`, XML, and UDT data in native mode are stored with a 4-byte prefix, like `text`, `image`, and `ntext` data, rather than with an 8-byte prefix, which is the default for [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and later versions.</span></span>  
  
## <a name="copying-date-values"></a><span data-ttu-id="eeea7-126">日付値のコピー</span><span class="sxs-lookup"><span data-stu-id="eeea7-126">Copying Date Values</span></span>  
 <span data-ttu-id="eeea7-127">**bcp** は ODBC 一括コピー API を使用します。</span><span class="sxs-lookup"><span data-stu-id="eeea7-127">**bcp** uses the ODBC bulk copy API.</span></span> <span data-ttu-id="eeea7-128">したがって、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 **bcp** に日付値をインポートするには、ODBC の日付形式 (*yyyy-mm-dd hh:mm:ss*[ *.f...* ]) を使用します。</span><span class="sxs-lookup"><span data-stu-id="eeea7-128">Therefore, to import date values into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp** uses the ODBC date format (*yyyy-mm-dd hh:mm:ss*[*.f...*]).</span></span>  
  
 <span data-ttu-id="eeea7-129">**Bcp**コマンドは、およびの値に対して ODBC の既定の形式を使用して、文字形式のデータファイルをエクスポートし `datetime` `smalldatetime` ます。</span><span class="sxs-lookup"><span data-stu-id="eeea7-129">The **bcp** command exports character format data files using the ODBC default format for `datetime` and `smalldatetime` values.</span></span> <span data-ttu-id="eeea7-130">たとえば、日付 `12 Aug 1998` が含まれた `datetime` 型の列は、文字列 `1998-08-12 00:00:00.000` としてデータ ファイルに一括コピーされます。</span><span class="sxs-lookup"><span data-stu-id="eeea7-130">For example, a `datetime` column containing the date `12 Aug 1998` is bulk copied to a data file as the character string `1998-08-12 00:00:00.000`.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="eeea7-131">Bcp を使用してフィールドにデータをインポートする場合は、 `smalldatetime` 秒の値が00.000 であることを確認してください。そうしないと、操作は失敗します。 **bcp**</span><span class="sxs-lookup"><span data-stu-id="eeea7-131">When importing data into a `smalldatetime` field using **bcp**, be sure the value for seconds is 00.000; otherwise the operation will fail.</span></span> <span data-ttu-id="eeea7-132">`smalldatetime` データ型には、最も近い "分" までの値のみが保持されます。</span><span class="sxs-lookup"><span data-stu-id="eeea7-132">The `smalldatetime` data type only holds values to the nearest minute.</span></span> <span data-ttu-id="eeea7-133">この場合、BULK INSERT および INSERT ... SELECT \* FROM OPENROWSET(BULK...) は失敗しませんが、秒の値は切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="eeea7-133">BULK INSERT and INSERT ... SELECT \* FROM OPENROWSET(BULK...) will not fail in this instance but will truncate the seconds value.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="eeea7-134">関連タスク</span><span class="sxs-lookup"><span data-stu-id="eeea7-134">Related Tasks</span></span>  
 <span data-ttu-id="eeea7-135">**一括インポートまたは一括エクスポートのデータ形式を使用するには**</span><span class="sxs-lookup"><span data-stu-id="eeea7-135">**To use data formats for bulk import or bulk export**</span></span>  
  
-   [<span data-ttu-id="eeea7-136">文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eeea7-136">Use Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="eeea7-137">ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eeea7-137">Use Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-native-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="eeea7-138">Unicode 文字形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eeea7-138">Use Unicode Character Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-character-format-to-import-or-export-data-sql-server.md)  
  
-   [<span data-ttu-id="eeea7-139">Unicode ネイティブ形式を使用したデータのインポートまたはエクスポート &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eeea7-139">Use Unicode Native Format to Import or Export Data &#40;SQL Server&#41;</span></span>](use-unicode-native-format-to-import-or-export-data-sql-server.md)  
  
 
  
## <a name="see-also"></a><span data-ttu-id="eeea7-140">参照</span><span class="sxs-lookup"><span data-stu-id="eeea7-140">See Also</span></span>  
 <span data-ttu-id="eeea7-141">[bcp ユーティリティ](../../tools/bcp-utility.md) </span><span class="sxs-lookup"><span data-stu-id="eeea7-141">[bcp Utility](../../tools/bcp-utility.md) </span></span>  
 <span data-ttu-id="eeea7-142">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eeea7-142">[BULK INSERT &#40;Transact-SQL&#41;](/sql/t-sql/statements/bulk-insert-transact-sql) </span></span>  
 <span data-ttu-id="eeea7-143">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eeea7-143">[OPENROWSET &#40;Transact-SQL&#41;](/sql/t-sql/functions/openrowset-transact-sql) </span></span>  
 <span data-ttu-id="eeea7-144">[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eeea7-144">[Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) </span></span>  
 <span data-ttu-id="eeea7-145">[SQL Server データベース エンジンの旧バージョンとの互換性](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span><span class="sxs-lookup"><span data-stu-id="eeea7-145">[SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md) </span></span>  
 [<span data-ttu-id="eeea7-146">CAST および CONVERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="eeea7-146">CAST and CONVERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/cast-and-convert-transact-sql)  
  
  
