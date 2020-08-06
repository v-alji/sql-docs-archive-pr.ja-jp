---
title: SQL Server Native Client OLE DB プロバイダーアプリケーションの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, application creation
- applications [SQL Server Native Client]
- OLE DB, creating applications
ms.assetid: f3ae6815-f32d-4913-a1a2-2ba2f20cfd88
author: rothja
ms.author: jroth
ms.openlocfilehash: a661f23cdacc4b581dadbe7625cb6e2ea318857f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714302"
---
# <a name="creating-a-sql-server-native-client-ole-db-provider-application"></a><span data-ttu-id="eccac-102">SQL Server Native Client OLE DB プロバイダー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="eccac-102">Creating a SQL Server Native Client OLE DB Provider Application</span></span>
  <span data-ttu-id="eccac-103">Native Client OLE DB プロバイダーアプリケーションを作成するには、次 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="eccac-103">Creating a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider application involves these steps:</span></span>  
  
1.  <span data-ttu-id="eccac-104">データ ソースへの接続の確立。</span><span class="sxs-lookup"><span data-stu-id="eccac-104">Establishing a connection to a data source.</span></span>  
  
2.  <span data-ttu-id="eccac-105">コマンドの実行。</span><span class="sxs-lookup"><span data-stu-id="eccac-105">Executing a command.</span></span>  
  
3.  <span data-ttu-id="eccac-106">結果の処理。</span><span class="sxs-lookup"><span data-stu-id="eccac-106">Processing the results.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eccac-107">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="eccac-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="eccac-108">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="eccac-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="eccac-109">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="eccac-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="eccac-110">資格情報を保存する必要がある場合は、[Win32 CryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="eccac-110">If you must persist credentials, you should encrypt them with [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eccac-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="eccac-111">In This Section</span></span>  
  
-   [<span data-ttu-id="eccac-112">データ ソースへの接続の確立</span><span class="sxs-lookup"><span data-stu-id="eccac-112">Establishing a Connection to a Data Source</span></span>](establishing-a-connection-to-a-data-source.md)  
  
-   [<span data-ttu-id="eccac-113">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="eccac-113">Executing a Command</span></span>](executing-a-command.md)  
  
-   [<span data-ttu-id="eccac-114">結果の処理</span><span class="sxs-lookup"><span data-stu-id="eccac-114">Processing Results</span></span>](processing-results.md)  
  
-   [<span data-ttu-id="eccac-115">OLE DB プロパティについて</span><span class="sxs-lookup"><span data-stu-id="eccac-115">About OLE DB Properties</span></span>](about-ole-db-properties.md)  
  
-   [<span data-ttu-id="eccac-116">SQL Server Native Client の OLE DB での OUTPUT 句の使用</span><span class="sxs-lookup"><span data-stu-id="eccac-116">Using the OUTPUT Clause with OLE DB in SQL Server Native Client</span></span>](using-the-output-clause-with-ole-db-in-sql-server-native-client.md)  
  
## <a name="see-also"></a><span data-ttu-id="eccac-117">参照</span><span class="sxs-lookup"><span data-stu-id="eccac-117">See Also</span></span>  
 [<span data-ttu-id="eccac-118">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="eccac-118">SQL Server Native Client &#40;OLE DB&#41;</span></span>](../native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
