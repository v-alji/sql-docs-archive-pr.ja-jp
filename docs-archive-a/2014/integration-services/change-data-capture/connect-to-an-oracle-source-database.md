---
title: Oracle ソース データベースへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- oraDb
ms.assetid: 220cf555-0db2-443c-8f87-8e413f3ca731
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fccba3d11adc67b3f5ef4f8648ec5d0de07a5648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720318"
---
# <a name="connect-to-an-oracle-source-database"></a><span data-ttu-id="94e0a-102">Oracle ソース データベースへの接続</span><span class="sxs-lookup"><span data-stu-id="94e0a-102">Connect to an Oracle Source Database</span></span>
  <span data-ttu-id="94e0a-103">[Oracle ソース] ページを使用すると、Oracle ソース データベースへの接続に必要な情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="94e0a-103">Use the Oracle Source page to provide the information necessary to connect to the Oracle source database.</span></span> <span data-ttu-id="94e0a-104">CDC インスタンスによって、接続している Oracle データベースの再実行ログが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="94e0a-104">The CDC instance will read the redo logs of the Oracle database you are connected to.</span></span>  
  
 <span data-ttu-id="94e0a-105">**[Oracle 接続文字列]**</span><span class="sxs-lookup"><span data-stu-id="94e0a-105">**Oracle Connect String**</span></span>  
 <span data-ttu-id="94e0a-106">使用している Oracle データベースがあるコンピューターへの Oracle 接続文字列を入力します。</span><span class="sxs-lookup"><span data-stu-id="94e0a-106">Enter the Oracle connect string to the computer with the Oracle database you are using.</span></span> <span data-ttu-id="94e0a-107">接続文字列は、次のいずれかの方法で記述されます。</span><span class="sxs-lookup"><span data-stu-id="94e0a-107">The connect string is written in one of the following ways:</span></span>  
  
 `host[:port][/service name]`  
  
 <span data-ttu-id="94e0a-108">接続文字列で Oracle Net 接続記述子を指定することもできます (例: `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span><span class="sxs-lookup"><span data-stu-id="94e0a-108">The connection string can also specify an Oracle Net connect descriptor, for example, `(DESCRIPTION=(ADDRESS=(PROTOCOL=tcp) (HOST=erp.contoso.com) (PORT=1521)) (CONNECT_DATA=(SERVICE_NAME=orcl)))`</span></span>  
  
 <span data-ttu-id="94e0a-109">ディレクトリ サーバーまたは tnsnames を使用している場合は、接続文字列を接続の名前にすることができます。</span><span class="sxs-lookup"><span data-stu-id="94e0a-109">If using a directory server or tnsnames, the connect string can be the name of the connection.</span></span>  
  
 <span data-ttu-id="94e0a-110">**[Oracle ログ マイニング認証]**</span><span class="sxs-lookup"><span data-stu-id="94e0a-110">**Oracle Log Mining Authentication**</span></span>  
 <span data-ttu-id="94e0a-111">ログ マイニングを承認されている Oracle データベース ユーザーの資格情報を入力するには、次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="94e0a-111">To enter the credentials for the Oracle database user that is authorized for log mining, select one of the following:</span></span>  
  
-   <span data-ttu-id="94e0a-112">**[Windows 認証]** : 現在の Windows ドメイン資格情報を使用する場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="94e0a-112">**Windows Authentication**: Select this to use the current Windows domain credentials.</span></span> <span data-ttu-id="94e0a-113">このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="94e0a-113">You can use this option only if the Oracle database is configured to work with Windows authentication.</span></span>  
  
-   <span data-ttu-id="94e0a-114">**[Oracle 認証]** : このオプションを選択する場合、接続先の Oracle データベースのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="94e0a-114">**Oracle Authentication**: If you select this option, you must type the **User Name** and **Password** for the user in the Oracle database you are connecting to.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94e0a-115">ユーザーがログ マイニング ユーザーになるには、Oracle データベースで次の特権を付与される必要があります。</span><span class="sxs-lookup"><span data-stu-id="94e0a-115">A user must have the following privileges granted in the Oracle database to be a log-mining user.</span></span>  
> 
>  -   <span data-ttu-id="94e0a-116">\<any-captured-table> に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-116">SELECT on \<any-captured-table></span></span>  
> -   <span data-ttu-id="94e0a-117">SELECT ANY TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="94e0a-117">SELECT ANY TRANSACTION</span></span>  
> -   <span data-ttu-id="94e0a-118">DBMS LOGMNR に対する EXECUTE</span><span class="sxs-lookup"><span data-stu-id="94e0a-118">EXECUTE on DBMS LOGMNR</span></span>  
> -   <span data-ttu-id="94e0a-119">V$LOGMNR CONTENTS に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-119">SELECT on V$LOGMNR CONTENTS</span></span>  
> -   <span data-ttu-id="94e0a-120">V$ARCHIVED LOG に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-120">SELECT on V$ARCHIVED LOG</span></span>  
> -   <span data-ttu-id="94e0a-121">V$LOG に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-121">SELECT on V$LOG</span></span>  
> -   <span data-ttu-id="94e0a-122">V$LOGFILE に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-122">SELECT on V$LOGFILE</span></span>  
> -   <span data-ttu-id="94e0a-123">V$DATABASE に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-123">SELECT on V$DATABASE</span></span>  
> -   <span data-ttu-id="94e0a-124">V$THREAD に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-124">SELECT on V$THREAD</span></span>  
> -   <span data-ttu-id="94e0a-125">ALL INDEXES に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-125">SELECT on ALL INDEXES</span></span>  
> -   <span data-ttu-id="94e0a-126">ALL OBJECTS に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-126">SELECT on ALL OBJECTS</span></span>  
> -   <span data-ttu-id="94e0a-127">DBA OBJECTS に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-127">SELECT on DBA OBJECTS</span></span>  
> -   <span data-ttu-id="94e0a-128">ALL TABLES に対する SELECT</span><span class="sxs-lookup"><span data-stu-id="94e0a-128">SELECT on ALL TABLES</span></span>  
> 
>  <span data-ttu-id="94e0a-129">これらの特権を V$xxx に付与できないときは、V_S$xxx に付与してください。</span><span class="sxs-lookup"><span data-stu-id="94e0a-129">If any of these privileges cannot be granted to a V$xxx, then grant them to the V_S$xxx.</span></span>  
  
 <span data-ttu-id="94e0a-130">**[接続テスト]**</span><span class="sxs-lookup"><span data-stu-id="94e0a-130">**Test Connection**</span></span>  
 <span data-ttu-id="94e0a-131">Oracle データベースがあるリモート コンピューターとの接続が確立されているかどうかを確認するには、 **[テスト接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="94e0a-131">Click **Test Connection** to determine whether you established a connection with the remote computer that has the Oracle database.</span></span> <span data-ttu-id="94e0a-132">接続が正常に確立されたかどうかを通知するダイアログ ボックスが開きます。</span><span class="sxs-lookup"><span data-stu-id="94e0a-132">A dialog box opens to inform you whether the connection was successful.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="94e0a-133">CDC デザイナーが管理者として実行されていない場合は、既知の問題のために Oracle ソース データベースとの接続が失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="94e0a-133">Due to a known issue connection to the Oracle source database may fail if the CDC Designer is not run as an administrator.</span></span> <span data-ttu-id="94e0a-134">接続が失敗した場合は、 **[管理者として実行]** オプションを使用して CDC デザイナーを終了して再起動します。</span><span class="sxs-lookup"><span data-stu-id="94e0a-134">If connection fails, close and restart the CDC Designer using the **Run as administrator** option.</span></span>  
  
 <span data-ttu-id="94e0a-135">このページでの情報入力が終了したら、 **[次へ]** をクリックして「 [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md)」に進みます。</span><span class="sxs-lookup"><span data-stu-id="94e0a-135">After you finish entering information on this page, click **Next** to [Select Oracle Tables and Columns](select-oracle-tables-and-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e0a-136">参照</span><span class="sxs-lookup"><span data-stu-id="94e0a-136">See Also</span></span>  
 <span data-ttu-id="94e0a-137">[SQL Server 変更データベース インスタンスを作成する方法](how-to-create-the-sql-server-change-database-instance.md) </span><span class="sxs-lookup"><span data-stu-id="94e0a-137">[How to Create the SQL Server Change Database Instance](how-to-create-the-sql-server-change-database-instance.md) </span></span>  
 [<span data-ttu-id="94e0a-138">インスタンスのプロパティの編集</span><span class="sxs-lookup"><span data-stu-id="94e0a-138">Edit Instance Properties</span></span>](edit-instance-properties.md)  
  
  
