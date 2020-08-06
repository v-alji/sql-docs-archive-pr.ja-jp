---
title: 文字データの自動変換 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- result sets [ODBC], autotranslating character data
- data types [ODBC], autotranslating character data
- ACPs
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- AutoTranslate feature
- ANSI code pages
- character data autotranslation [ODBC]
- autotranslating character data
- SQL Server Native Client ODBC driver, data types
- ODBC data types, autotranslating character data
ms.assetid: 86a8adda-c5ad-477f-870f-cb370c39ee13
author: rothja
ms.author: jroth
ms.openlocfilehash: 91dd1714d553f201c1cab78bbca77d2445b42923
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741982"
---
# <a name="autotranslation-of-character-data"></a><span data-ttu-id="566b7-102">文字データの自動変換</span><span class="sxs-lookup"><span data-stu-id="566b7-102">Autotranslation of Character Data</span></span>
  <span data-ttu-id="566b7-103">SQL_C_CHAR で宣言された ANSI 文字変数や、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **CHAR**、 **varchar**、または**text**データ型を使用してに格納されているデータなどの文字データは、制限された文字数のみを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="566b7-103">Character data, such as ANSI character variables declared with SQL_C_CHAR or data stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using the **char**, **varchar**, or **text** data types, can represent only a limited number of characters.</span></span> <span data-ttu-id="566b7-104">1 文字ごとに 1 バイトを使用して保存される文字データでは、256 文字しか表現できません。</span><span class="sxs-lookup"><span data-stu-id="566b7-104">Character data stored using one byte per character can only represent 256 characters.</span></span> <span data-ttu-id="566b7-105">SQL_C_CHAR 変数に格納される値は、クライアント コンピューターの ANSI コード ページ (ACP) を使用して解釈されます。</span><span class="sxs-lookup"><span data-stu-id="566b7-105">The values stored in SQL_C_CHAR variables are interpreted using the ANSI code page (ACP) of the client computer.</span></span> <span data-ttu-id="566b7-106">サーバーで**char**、 **varchar**、または**text**データ型を使用して格納されている値は、サーバーの ACP を使用して評価されます。</span><span class="sxs-lookup"><span data-stu-id="566b7-106">The values stored using **char**, **varchar**, or **text** data types on the server are evaluated using the ACP of the server.</span></span>  
  
 <span data-ttu-id="566b7-107">サーバーとクライアントの両方に同じ ACP がある場合、SQL_C_CHAR、 **CHAR**、 **varchar**、または**text**オブジェクトに格納されている値の解釈に問題はありません。</span><span class="sxs-lookup"><span data-stu-id="566b7-107">If both the server and the client have the same ACP, then they have no problems in interpreting the values stored in SQL_C_CHAR, **char**, **varchar**, or **text** objects.</span></span> <span data-ttu-id="566b7-108">サーバーとクライアントの ACPs が異なる場合、 **CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターで使用されている場合、クライアントからの SQL_C_CHAR データはサーバー上で別の文字として解釈される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="566b7-108">If the server and client have different ACPs, then SQL_C_CHAR data from the client may be interpreted as a different character on the server if it is used in **char**, **varchar**, or **text** columns, variables, or parameters.</span></span> <span data-ttu-id="566b7-109">たとえば、値0xA5 を含む文字バイトは、文字として解釈されますか?</span><span class="sxs-lookup"><span data-stu-id="566b7-109">For example, a character byte containing the value 0xA5 is interpreted as the character ??</span></span> <span data-ttu-id="566b7-110">コードページ437を使用するコンピューターでは、コードページ1252を実行しているコンピューターでは、円記号 (??) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="566b7-110">on a computer using code page 437 and is interpreted as the yen sign (??) on a computer running code page 1252.</span></span>  
  
 <span data-ttu-id="566b7-111">Unicode データは、1 文字あたり 2 バイトを使用して格納されます。</span><span class="sxs-lookup"><span data-stu-id="566b7-111">Unicode data is stored using two bytes per character.</span></span> <span data-ttu-id="566b7-112">Unicode の仕様は、すべての拡張文字を網羅しています。したがって、すべての Unicode 文字は、すべてのコンピューターで同じ文字に解釈されます。</span><span class="sxs-lookup"><span data-stu-id="566b7-112">All extended characters are covered by the Unicode specification, so all Unicode characters are interpreted the same by all computers.</span></span>  
  
 <span data-ttu-id="566b7-113">Native Client ODBC ドライバーの AutoTranslate 機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クライアントと異なるコードページを持つサーバー間での文字データの移動に関する問題を最小限に抑えようとしています。</span><span class="sxs-lookup"><span data-stu-id="566b7-113">The AutoTranslate feature of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to minimize the problems in moving character data between a client and a server that have different code pages.</span></span> <span data-ttu-id="566b7-114">AutoTranslate は、 [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md)の接続文字列、 [sqlconfigdatasource](../native-client-odbc-api/sqlconfigdatasource.md)の構成文字列、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] odbc アドミニストレーターを使用して Native Client ODBC ドライバーのデータソースを構成するときに設定できます。</span><span class="sxs-lookup"><span data-stu-id="566b7-114">AutoTranslate can be set in the connect string of [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md), in the configuration string of [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md), or when configuring data sources for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver using ODBC Administrator.</span></span>  
  
 <span data-ttu-id="566b7-115">AutoTranslate が "no" に設定されている場合、クライアントの SQL_C_CHAR 変数と、データベースの**CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターの間で移動されたデータの変換は行われません [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="566b7-115">When AutoTranslate is set to "no", no conversions are done on data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="566b7-116">この場合、データに拡張文字が含まれていて、クライアント コンピューターとサーバー コンピューターのコード ページが異なっていると、ビット パターンはクライアントとサーバーでは異なって解釈される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="566b7-116">The bit patterns may be interpreted differently on the client and server computers if the data contains extended characters and the two computers have different code pages.</span></span> <span data-ttu-id="566b7-117">クライアントとサーバーが同じコード ページを使用している場合は、データは同じ文字に解釈されます。</span><span class="sxs-lookup"><span data-stu-id="566b7-117">The data will be interpreted the same if both computers have the same code page.</span></span>  
  
 <span data-ttu-id="566b7-118">AutoTranslate が "yes" に設定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは Unicode を使用して、クライアント上の SQL_C_CHAR 変数と、データベース内の**CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターの間で移動されたデータを変換し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="566b7-118">When AutoTranslate is set to "yes", the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses Unicode to convert data moved between SQL_C_CHAR variables on the client and **char**, **varchar**, or **text** columns, variables, or parameters in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database:</span></span>  
  
-   <span data-ttu-id="566b7-119">データがクライアントの SQL_C_CHAR 変数から**CHAR**、 **varchar**、または**text**型の列、変数、またはパラメーターにデータベースで送信されると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、ODBC ドライバーはまず、クライアントの Acp を使用して SQL_C_CHAR から unicode に変換し、次にサーバーの acp を使用して unicode から文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="566b7-119">When data is sent from an SQL_C_CHAR variable on the client to a **char**, **varchar**, or **text** column, variable, or parameter in an [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, the ODBC driver first converts from SQL_C_CHAR to Unicode using the ACP of the client, then from Unicode back to character using the ACP of the server.</span></span>  
  
-   <span data-ttu-id="566b7-120">データベース内の**char**、 **varchar**、または**text**型の列、変数、またはパラメーターから、データがクライアントの SQL_C_CHAR 変数に送信されると [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、まずサーバーの acp を使用して文字を unicode に変換し、次に unicode からクライアントの acp を使用して SQL_C_CHAR します。</span><span class="sxs-lookup"><span data-stu-id="566b7-120">When data is sent from a **char**, **varchar**, or **text** column, variable, or parameter in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database to a SQL_C_CHAR variable on the client, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver first converts from character to Unicode using the ACP of the server, then from Unicode back to SQL_C_CHAR using the ACP of the client.</span></span>  
  
 <span data-ttu-id="566b7-121">これらの変換はすべて、クライアントで実行されている Native Client ODBC ドライバーによって行われるため [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、サーバーの ACP はクライアントコンピューターにインストールされているコードページの1つである必要があります。</span><span class="sxs-lookup"><span data-stu-id="566b7-121">Because all of these conversions are done by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver executing on the client, the server ACP must be one of the code pages installed on the client computer.</span></span>  
  
 <span data-ttu-id="566b7-122">Unicode を使用して文字を変換することで、両方のコード ページに存在しているすべての文字を適切に変換できます。</span><span class="sxs-lookup"><span data-stu-id="566b7-122">Making the character conversions through Unicode ensures the proper conversion of all characters that exist in both code pages.</span></span> <span data-ttu-id="566b7-123">ただし、一方のコード ページにあっても、他方のコード ページにない文字の場合は、変換先のコード ページでは表現できません。</span><span class="sxs-lookup"><span data-stu-id="566b7-123">If a character exists in one code page but not another, however, then the character cannot be represented in the target code page.</span></span> <span data-ttu-id="566b7-124">たとえば、コードページ1252には、商標記号 (??) が登録されていますが、コードページ437にはありません。</span><span class="sxs-lookup"><span data-stu-id="566b7-124">For example, code page 1252 has the registered trademark symbol (??), while code page 437 does not.</span></span>  
  
 <span data-ttu-id="566b7-125">AutoTranslate の設定は、次の変換には影響しません。</span><span class="sxs-lookup"><span data-stu-id="566b7-125">The AutoTranslate setting has no effect on these conversions:</span></span>  
  
-   <span data-ttu-id="566b7-126">データベース内の文字 SQL_C_CHAR クライアント変数と Unicode **nchar**、 **nvarchar**、または**ntext**型の列、変数、またはパラメーターの間でデータを移動する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="566b7-126">Moving data between character SQL_C_CHAR client variables and Unicode **nchar**, **nvarchar**, or **ntext** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
-   <span data-ttu-id="566b7-127">Unicode SQL_C_WCHAR クライアント変数と、データベース内の文字**char**、 **varchar**、または**text**型の列、変数、またはパラメーターの間でデータを移動する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="566b7-127">Moving data between Unicode SQL_C_WCHAR client variables and character **char**, **varchar**, or **text** columns, variables, or parameters in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
 <span data-ttu-id="566b7-128">文字から Unicode にデータが移動される場合、データは必ず変換されます。</span><span class="sxs-lookup"><span data-stu-id="566b7-128">Data always must be converted when moved from character to Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="566b7-129">参照</span><span class="sxs-lookup"><span data-stu-id="566b7-129">See Also</span></span>  
 <span data-ttu-id="566b7-130">[ODBC&#41;&#40;結果の処理](processing-results-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="566b7-130">[Processing Results &#40;ODBC&#41;](processing-results-odbc.md) </span></span>  
 [<span data-ttu-id="566b7-131">照合順序と Unicode のサポート</span><span class="sxs-lookup"><span data-stu-id="566b7-131">Collation and Unicode Support</span></span>](../collations/collation-and-unicode-support.md)  
  
  
