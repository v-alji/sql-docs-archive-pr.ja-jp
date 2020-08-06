---
title: セッション言語の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], international considerations
- globalization [SQL Server], sessions
- time [SQL Server]
- sessions [SQL Server], languages
- international considerations [SQL Server], sessions
- dates [SQL Server], session languages
- global considerations [SQL Server], sessions
- client-side session language
- time [SQL Server], session languages
- messages [SQL Server], international considerations
- server-side session language
ms.assetid: de7f2c90-8f4f-4cfc-94cc-4933a7fd2bde
author: stevestein
ms.author: sstein
ms.openlocfilehash: da8d6adce66ac5b97e533b5afaefabda40e4b966
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645664"
---
# <a name="set-a-session-language"></a><span data-ttu-id="5ea40-102">セッション言語の設定</span><span class="sxs-lookup"><span data-stu-id="5ea40-102">Set a Session Language</span></span>
  <span data-ttu-id="5ea40-103">セッション言語は、言語とカルチャの設定に基づいて、次の要素がサーバー上でどのように表示されるかを設定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-103">The session language can be used to set how the following elements are displayed on the server, based on language and cultural preference:</span></span>  
  
-   <span data-ttu-id="5ea40-104">エラーとその他のシステム メッセージで使用される言語。</span><span class="sxs-lookup"><span data-stu-id="5ea40-104">The language that will be used for error and other system messages.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="5ea40-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できるすべての言語で、すべてのシステム エラー文字列とシステム メッセージの複数のコピーを保持できます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-105">supports having multiple copies of all system error strings and messages in all the languages in which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is available.</span></span> <span data-ttu-id="5ea40-106">このようなメッセージは、 [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) カタログ ビューに表示できます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-106">These messages can be viewed in the [sys.messages](/sql/relational-databases/system-catalog-views/messages-for-errors-catalog-views-sys-messages) catalog view.</span></span> <span data-ttu-id="5ea40-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のローカライズ版をインストールすると、これらのシステム メッセージが、インストールする言語バージョン用に変換されます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-107">When you install a localized version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], these system messages are translated for the language version that you install.</span></span> <span data-ttu-id="5ea40-108">既定では、これらのメッセージの英語 (U.S.) セットも取得されます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-108">By default, you also obtain the U.S. English set of these messages.</span></span> <span data-ttu-id="5ea40-109">さらに、 [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql)を使用して、特定の言語のユーザー定義メッセージを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-109">Additionally, you can add user-defined messages in a specific language by using [sp_addmessage](/sql/relational-databases/system-stored-procedures/sp-addmessage-transact-sql).</span></span>  
  
-   <span data-ttu-id="5ea40-110">日付と時刻のデータの形式</span><span class="sxs-lookup"><span data-stu-id="5ea40-110">The format of date and time data.</span></span>  
  
-   <span data-ttu-id="5ea40-111">略記を含む、曜日と月の名前</span><span class="sxs-lookup"><span data-stu-id="5ea40-111">The names of days and months, including abbreviations.</span></span>  
  
-   <span data-ttu-id="5ea40-112">週の最初の曜日</span><span class="sxs-lookup"><span data-stu-id="5ea40-112">The first day of the week.</span></span>  
  
-   <span data-ttu-id="5ea40-113">通貨データ</span><span class="sxs-lookup"><span data-stu-id="5ea40-113">Currency data.</span></span>  
  
 <span data-ttu-id="5ea40-114">セッション設定として 33 種類の言語を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-114">There are 33 languages available for use as session settings.</span></span> <span data-ttu-id="5ea40-115">言語の一覧については、「 [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ea40-115">For a list of languages, see [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-server"></a><span data-ttu-id="5ea40-116">サーバーからのセッション言語の設定</span><span class="sxs-lookup"><span data-stu-id="5ea40-116">Setting the Session Language from the Server</span></span>  
 <span data-ttu-id="5ea40-117">セッション言語をサーバー側から設定するには、 [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ea40-117">To set the session language from the server side, use [SET LANGUAGE](/sql/t-sql/statements/set-language-transact-sql).</span></span>  
  
## <a name="setting-the-session-language-from-the-client"></a><span data-ttu-id="5ea40-118">クライアントからのセッション言語の設定</span><span class="sxs-lookup"><span data-stu-id="5ea40-118">Setting the Session Language from the Client</span></span>  
 <span data-ttu-id="5ea40-119">セッション言語は、OLE DB、ODBC、または ADO.NET を使用してクライアント側で設定できます。</span><span class="sxs-lookup"><span data-stu-id="5ea40-119">The session language can be set on the client side by using OLE DB, ODBC or ADO.NET.</span></span> <span data-ttu-id="5ea40-120">OLE DB の場合は、SSPROP_INIT_CURRENTLANGUAGE プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ea40-120">For OLE DB, use the SSPROP_INIT_CURRENTLANGUAGE property.</span></span> <span data-ttu-id="5ea40-121">詳細については、「「 [初期化プロパティと承認プロパティ](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ea40-121">For more information, see [Initialization and Authorization Properties](../native-client-ole-db-data-source-objects/initialization-and-authorization-properties.md).</span></span>  
  
 <span data-ttu-id="5ea40-122">ODBC の場合は、Language キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ea40-122">For ODBC, use the Language keyword.</span></span> <span data-ttu-id="5ea40-123">詳細については、「 [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ea40-123">For more information, see [SQLConfigDataSource](../native-client-odbc-api/sqlconfigdatasource.md).</span></span>  
  
 <span data-ttu-id="5ea40-124">ADO.NET の場合は、 **ConnectionString** オブジェクトの **Current Language** パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ea40-124">For ADO.NET, use the **Current Language** parameter of the **ConnectionString** object.</span></span> <span data-ttu-id="5ea40-125">詳細については、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) ソフトウェア開発キット (SDK) のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ea40-125">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Data Access Components (MDAC) software development kit (SDK) documentation.</span></span>  
  
  
