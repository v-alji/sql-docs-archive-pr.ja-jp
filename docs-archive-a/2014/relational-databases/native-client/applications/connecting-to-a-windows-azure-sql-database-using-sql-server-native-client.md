---
title: SQL Server Native Client | を使用した Azure SQL Database への接続Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 0dc20bb6-b142-4259-b87b-427d2ba798af
author: rothja
ms.author: jroth
ms.openlocfilehash: 177c655f97e32f2044460e87c6cd775cdf8fcde9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642038"
---
# <a name="connecting-to-an-azure-sql-database-using-sql-server-native-client"></a><span data-ttu-id="29fe6-102">SQL Server Native Client を使用した Azure SQL データベースへの接続</span><span class="sxs-lookup"><span data-stu-id="29fe6-102">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>
  <span data-ttu-id="29fe6-103">Native Client を使用してに接続する方法を示すサンプルについ [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ては、「[開発: 操作方法に関するトピック (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29fe6-103">For a sample that shows how to connect to a [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, see [Development: How-to Topics (Azure SQL Database)](https://msdn.microsoft.com/library/ee621787.aspx).</span></span>  
  
## <a name="known-issues-when-connecting-to-a-sql-database"></a><span data-ttu-id="29fe6-104">SQL データベースに接続するときの既知の問題</span><span class="sxs-lookup"><span data-stu-id="29fe6-104">Known Issues When Connecting to a SQL Database</span></span>  
 <span data-ttu-id="29fe6-105">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続する場合、次のような既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="29fe6-105">The following are known issues when connecting to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client:</span></span>  
  
-   <span data-ttu-id="29fe6-106">各段階で `SQLBrowseConnect` が使用されている場合、`SQLBrowseConnect` との接続が拒否される可能性がある。</span><span class="sxs-lookup"><span data-stu-id="29fe6-106">A connection made with `SQLBrowseConnect` may be rejected if `SQLBrowseConnect` is used in stages.</span></span>  <span data-ttu-id="29fe6-107">たとえば、最初の通話でドライバー名が送信され、サーバーと資格情報 (ユーザー名とパスワード) が 2 番目の通話で送信されて接続が確立し、データベース名と言語が 3 番目の通話で送信されたとします。</span><span class="sxs-lookup"><span data-stu-id="29fe6-107">For example, if the driver name is sent in the first call, server and credentials (user and password) sent in the second call, establishing the connection, and a database name and a language in the third call.</span></span>  <span data-ttu-id="29fe6-108">3 番目の通話によって、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は USE ステートメントを発行してデータベースを変更します。</span><span class="sxs-lookup"><span data-stu-id="29fe6-108">The third call will cause [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to issue a USE statement to change databases.</span></span> <span data-ttu-id="29fe6-109">しかし、USE ステートメントは [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] ではサポートされないため、次のエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="29fe6-109">However, the USE statement is not supported in [!INCLUDE[ssSDS](../../../includes/sssds-md.md)], generating the following error:</span></span>  
  
    ```  
    [Microsoft][SQL Server Native Client 11.0][SQL Server]USE statement is not supported to switch between databases. Use a new connection to connect to a different Database.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="29fe6-110">参照</span><span class="sxs-lookup"><span data-stu-id="29fe6-110">See Also</span></span>  
 [<span data-ttu-id="29fe6-111">SQL Server Native Client を使用したアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="29fe6-111">Building Applications with SQL Server Native Client</span></span>](building-applications-with-sql-server-native-client.md)  
  
  
