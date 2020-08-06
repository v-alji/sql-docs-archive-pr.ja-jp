---
title: CLR 統合の新&#39;Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
ms.assetid: 871fcccd-b726-4b13-9f95-d02b4b39d8ab
author: rothja
ms.author: jroth
ms.openlocfilehash: b51eb5d8bee5ff8e514f294d5e9facca93a30bfa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640083"
---
# <a name="what39s-new-in-clr-integration"></a><span data-ttu-id="58221-102">CLR 統合の新機能&#39;</span><span class="sxs-lookup"><span data-stu-id="58221-102">What&#39;s New in CLR Integration</span></span>
  <span data-ttu-id="58221-103">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の CLR 統合で新しくなった点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="58221-103">The following are new features in CLR integration in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:</span></span>  
  
-   <span data-ttu-id="58221-104">CLR のバージョン 4 では、破損状態の例外を CLR データベース オブジェクトはキャッチしません。</span><span class="sxs-lookup"><span data-stu-id="58221-104">In version 4 of the CLR, CLR database objects no longer catch corrupted state exceptions.</span></span> <span data-ttu-id="58221-105">これらの例外は、CLR 統合ホスト層でキャッチされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="58221-105">These exceptions are now caught in the CLR integration hosting layer.</span></span> <span data-ttu-id="58221-106">これらの例外は、コード属性 ([ \<legacyCorruptedStateExceptionsPolicy> 要素](https://go.microsoft.com/fwlink/?LinkId=204954)) を設定することによって、CLR データベースコンポーネントによってキャッチされることがあります。</span><span class="sxs-lookup"><span data-stu-id="58221-106">These exceptions can still be caught by the CLR database components by setting a code attribute ([\<legacyCorruptedStateExceptionsPolicy> Element](https://go.microsoft.com/fwlink/?LinkId=204954)).</span></span> <span data-ttu-id="58221-107">ただし、破損状態の例外が発生した場合の結果には信頼性がないため、この設定はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="58221-107">However, this is not recommended because results are not reliable when a corrupted state exception occurs.</span></span>  
  
-   <span data-ttu-id="58221-108">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] には厳しいセキュリティ要件があるため、CLR データベース コンポーネントには、今後も CLR バージョン 2.0 で定義されたコード アクセス セキュリティ モデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="58221-108">Due to the strict security requirements of [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], CLR database components will continue to use the Code Access Security model defined in CLR version 2.0.</span></span>  
  
-   <span data-ttu-id="58221-109">CLR バージョン 4 では、`System.TimeSpan` 値の形式に誤りがあると、`System.FormatExceptions` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="58221-109">In CLR version 4, a format error in a `System.TimeSpan` value will generate a `System.FormatExceptions`.</span></span> <span data-ttu-id="58221-110">バージョン 4 未満の CLR では、`System.TimeSpan` 値の形式に誤りがあっても無視されていました。</span><span class="sxs-lookup"><span data-stu-id="58221-110">Prior to version 4 of the CLR, a format error in a `System.TimeSpan` value was ignored.</span></span> <span data-ttu-id="58221-111">CLR バージョン 4 未満の動作に依存するデータベース アプリケーションは、データベース互換性レベル (`ALTER DATABASE Compatibility Level`) を 100 以下にして実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58221-111">Database applications that rely on the behavior prior to version 4 of the CLR should run with a database compatibility level (`ALTER DATABASE Compatibility Level`) of 100 or lower.</span></span> <span data-ttu-id="58221-112">詳細については、「 [<TimeSpan_LegacyFormatMode> 要素](https://go.microsoft.com/fwlink/?LinkId=205109)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58221-112">For more information, see [<TimeSpan_LegacyFormatMode> Element](https://go.microsoft.com/fwlink/?LinkId=205109).</span></span>  
  
-   <span data-ttu-id="58221-113">CLR のバージョン 4 は、Unicode 5.1 をサポートします。</span><span class="sxs-lookup"><span data-stu-id="58221-113">Version 4 of the CLR supports Unicode 5.1.</span></span> <span data-ttu-id="58221-114">アクセントや記号を含んだ並べ替えの処理が改善されます。</span><span class="sxs-lookup"><span data-stu-id="58221-114">Sort operations involving some accent marks and symbols will be improved.</span></span> <span data-ttu-id="58221-115">従来の並べ替え動作に依存したアプリケーションでは、互換性の問題が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="58221-115">Compatibility problems may occur if your application relies on legacy sorting behavior.</span></span> <span data-ttu-id="58221-116">従来の並べ替え動作を有効にするには、データベース互換性レベル (`ALTER DATABASE Compatibility Level`) を 100 以下に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58221-116">To enable legacy sorting, the database compatibility level (`ALTER DATABASE Compatibility Level`) must be set to 100 or lower.</span></span> <span data-ttu-id="58221-117">この点をサポートするために、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] では、.NET Framework 4 ディレクトリ (C:\Windows\Microsoft.NET\Framework\v4.0.30319) に sort00001000.dll がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="58221-117">To support this, [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] will install sort00001000.dll in the .NET Framework 4 directory (C:\Windows\Microsoft.NET\Framework\v4.0.30319).</span></span> <span data-ttu-id="58221-118">詳細については、[\<CompatSortNLSVersion> 要素](https://go.microsoft.com/fwlink/?LinkId=205110)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="58221-118">For more information, see [\<CompatSortNLSVersion> Element](https://go.microsoft.com/fwlink/?LinkId=205110).</span></span>  
  
-   <span data-ttu-id="58221-119">次の列が、 [sys. dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql)に追加されました: `total_processor_time_ms` 、 `total_allocated_memory_kb` 、および `survived_memory_kb` 。</span><span class="sxs-lookup"><span data-stu-id="58221-119">The following columns have been added to [sys.dm_clr_appdomains](/sql/relational-databases/system-dynamic-management-views/sys-dm-clr-appdomains-transact-sql): `total_processor_time_ms`, `total_allocated_memory_kb`, and `survived_memory_kb`.</span></span>  
  
  
