---
title: データベース表現 (表形式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c327e07685e98e6fa9f992025510e869d909e5ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634687"
---
# <a name="database-representationtabular"></a><span data-ttu-id="be815-102">データベース表現 (テーブル)</span><span class="sxs-lookup"><span data-stu-id="be815-102">Database Representation(Tabular)</span></span>
  <span data-ttu-id="be815-103">テーブル モードでは、データベースは、テーブル モデル内に存在するすべてのオブジェクトを対象にするコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="be815-103">In Tabular Mode, the database is the container for all objects in the tabular model.</span></span>  
  
## <a name="database-representation"></a><span data-ttu-id="be815-104">データベース表現</span><span class="sxs-lookup"><span data-stu-id="be815-104">Database Representation</span></span>  
 <span data-ttu-id="be815-105">データベースは、テーブル モデルを構成するすべてのオブジェクトが格納される場所です。</span><span class="sxs-lookup"><span data-stu-id="be815-105">The database is the place where all objects that form a tabular model reside.</span></span> <span data-ttu-id="be815-106">開発者は、データベースに含まれている、接続、テーブル、ロールなどのオブジェクトを検索します。</span><span class="sxs-lookup"><span data-stu-id="be815-106">Contained by the database, the developer finds objects like connections, tables, roles and many more.</span></span>  
  
### <a name="database-in-amo"></a><span data-ttu-id="be815-107">AMO 内のデータベース</span><span class="sxs-lookup"><span data-stu-id="be815-107">Database in AMO</span></span>  
 <span data-ttu-id="be815-108">AMO を使用してテーブル モデル データベースを管理する場合、AMO 内の <xref:Microsoft.AnalysisServices.Database> オブジェクトは、テーブル モデル内のデータベース論理オブジェクトと一対一で対応します。</span><span class="sxs-lookup"><span data-stu-id="be815-108">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.Database> object in AMO matches one-to-one the database logical object in a tabular model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="be815-109">AMO 内でデータベース オブジェクトにアクセスするには、ユーザーがサーバー オブジェクトに対するアクセス権を得て、そこに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be815-109">In order to gain access to a database object, in AMO, the user needs to have access to a server object and connect to it.</span></span>  
  
### <a name="database-in-adomdnet"></a><span data-ttu-id="be815-110">ADOMD.Net 内のデータベース</span><span class="sxs-lookup"><span data-stu-id="be815-110">Database in ADOMD.Net</span></span>  
 <span data-ttu-id="be815-111">ADOMD を使用してテーブル モデル データベースを参照してクエリを実行する場合は、<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> オブジェクトを使用して、特定のデータベースへの接続を取得します。</span><span class="sxs-lookup"><span data-stu-id="be815-111">When using ADOMD to consult and query a tabular model database, connection to a specific database is obtained through the <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> object.</span></span>  
  
 <span data-ttu-id="be815-112">次のコードスニペットを使用して、特定のデータベースに直接接続できます。</span><span class="sxs-lookup"><span data-stu-id="be815-112">You can connect directly to a certain database using the following code snippet:</span></span>  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
...  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
...  
  
```  
  
 <span data-ttu-id="be815-113">また、次のコード スニペットを使用すると、既存の接続オブジェクト (閉じられていないもの) を利用して、現在のデータベースを別のデータベースに変更することができます。</span><span class="sxs-lookup"><span data-stu-id="be815-113">Also, over an existing connection object (that hasn't been closed), you can change the current database to another as shown in the following code snippet:</span></span>  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a><span data-ttu-id="be815-114">AMO 内のデータベース</span><span class="sxs-lookup"><span data-stu-id="be815-114">Database in AMO</span></span>  
 <span data-ttu-id="be815-115">AMO を使用してデータベース オブジェクトを管理する場合は、<xref:Microsoft.AnalysisServices.Server> オブジェクトの作業を開始します。</span><span class="sxs-lookup"><span data-stu-id="be815-115">When using AMO to manage a database object, start with a <xref:Microsoft.AnalysisServices.Server> object.</span></span> <span data-ttu-id="be815-116">その後、データベース コレクション内でデータベースを検索するか、コレクションに 1 つのデータベースを追加して新しいデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="be815-116">Then search for your database in the databases collection or create a new database by adding one to the collection.</span></span>  
  
 <span data-ttu-id="be815-117">次のコードスニペットは、データベースが存在しないことを確認した後、サーバーに接続して空のデータベースを作成する手順を示しています。</span><span class="sxs-lookup"><span data-stu-id="be815-117">The following code snippet shows the steps to connect to a server and create an empty database, after checking the database doesn't exist:</span></span>  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 <span data-ttu-id="be815-118">AMO を使用してデータベース表現の作成と操作を行う方法を実際の使用に際して理解するには、Tabular AMO 2012 サンプルのソース コードを参照してください。特に、ソース ファイル Database.cs の内容に注意してください。</span><span class="sxs-lookup"><span data-stu-id="be815-118">For a practical understanding on how to use AMO to create and manipulate database representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="be815-119">サンプル コードは、ここで説明する論理的概念をサポートする目的でのみ提供されるものであり、運用環境では使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="be815-119">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
