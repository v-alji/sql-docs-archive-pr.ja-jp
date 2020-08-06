---
title: 接続表現 (表形式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4b410b16-d36e-4185-bb20-922e66e5e2b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 60f3fdc10baf5dc3be9cd1b0ee6196d2a8da3d2f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634689"
---
# <a name="connection-representation-tabular"></a><span data-ttu-id="6f0e8-102">接続表現 (表形式)</span><span class="sxs-lookup"><span data-stu-id="6f0e8-102">Connection Representation (Tabular)</span></span>
  <span data-ttu-id="6f0e8-103">接続オブジェクトは、テーブル モデルに入力されるデータのソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="6f0e8-103">The connection object defines the source of the data that populates the tabular model.</span></span>  
  
## <a name="connection-representation"></a><span data-ttu-id="6f0e8-104">接続表現</span><span class="sxs-lookup"><span data-stu-id="6f0e8-104">Connection Representation</span></span>  
 <span data-ttu-id="6f0e8-105">接続オブジェクトの仕様は、OLE DB プロバイダーの規則に従います。</span><span class="sxs-lookup"><span data-stu-id="6f0e8-105">The specification for the connection object follows the rules of OLE DB providers.</span></span>  
  
### <a name="connection-in-amo"></a><span data-ttu-id="6f0e8-106">AMO 内の接続</span><span class="sxs-lookup"><span data-stu-id="6f0e8-106">Connection in AMO</span></span>  
 <span data-ttu-id="6f0e8-107">AMO を使用してテーブル モデル データベースを管理する場合、AMO 内の <xref:Microsoft.AnalysisServices.DataSource> オブジェクトは、接続論理オブジェクトと一対一で対応します。</span><span class="sxs-lookup"><span data-stu-id="6f0e8-107">When using AMO to manage a tabular model database, the <xref:Microsoft.AnalysisServices.DataSource> object in AMO matches one-to-one to the connection logical object.</span></span>  
  
 <span data-ttu-id="6f0e8-108">次のコード スニペットは、AMO データ ソース、またはテーブル モデルの Connection オブジェクトを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6f0e8-108">The following code snippet shows how to create an AMO data source, or Connection object in a tabular model.</span></span>  
  
```  
  
//Create an OLEDB connection string  
StringBuilder SqlCnxStr = new StringBuilder();  
SqlCnxStr.Append(String.Format("Data Source={0};" ,SQLServer.Text));  
SqlCnxStr.Append(String.Format("Initial Catalog={0};", SQLDatabase.Text));  
SqlCnxStr.Append(String.Format("Persist Security Info={0};", false));  
SqlCnxStr.Append(String.Format("Integrated Security={0};", "SSPI"));  
SqlCnxStr.Append(String.Format("Provider={0}", "SQLNCLI11"));  
String DatasourceCnxString = SqlCnxStr.ToString();  
  
//Verify connection string and connectivity  
System.Data.OleDb.OleDbConnection OleDbCnx = new System.Data.OleDb.OleDbConnection(DatasourceCnxString);  
try  
{  
    OleDbCnx.Open();  
}  
catch ()  
{  
    throw;  
}  
String newDataSourceName = (string.IsNullOrEmpty(DataSourceName.Text) || string.IsNullOrWhiteSpace(DataSourceName.Text)) ? SQLDatabase.Text : DataSourceName.Text;  
AMO.DataSource newDatasource = newDatabase.DataSources.Add(newDataSourceName, newDataSourceName);  
newDatasource.ConnectionString = DatasourceCnxString.Text;  
if (impersonateServiceAccount.Checked)  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateServiceAccount);  
else  
{  
    if (String.IsNullOrEmpty(impersonateAccountUserName.Text))  
    {  
        MessageBox.Show(String.Format("Account User Name cannot be blank when using 'ImpersonateAccount' mode"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        return;  
    }  
    newDatasource.ImpersonationInfo = new AMO.ImpersonationInfo(AMO.ImpersonationMode.ImpersonateAccount, impersonateAccountUserName.Text, impersonateAccountPassword.Text);  
}  
newDatasource.Update();  
  
```  
  
## <a name="tabular-amo-2012-sample"></a><span data-ttu-id="6f0e8-109">Tabular AMO 2012 サンプル</span><span class="sxs-lookup"><span data-stu-id="6f0e8-109">Tabular AMO 2012 sample</span></span>  
 <span data-ttu-id="6f0e8-110">AMO を使用して接続表現の作成と操作を行う方法について理解を深めるには、Tabular AMO 2012 サンプルのソース コードを参照してください。特に、ソース ファイル Database.cs の内容に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6f0e8-110">To have a better understanding on how to use AMO to create and manipulate connection representations, see source code in the Tabular AMO 2012 sample; specifically check in the following source file: Database.cs.</span></span> <span data-ttu-id="6f0e8-111">このサンプルは、Codeplex から入手できます。</span><span class="sxs-lookup"><span data-stu-id="6f0e8-111">The sample is available at Codeplex.</span></span> <span data-ttu-id="6f0e8-112">サンプル コードは、ここで説明する論理的概念をサポートする目的でのみ提供されるものであり、運用環境では使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="6f0e8-112">Sample code is provided only as a support to the logical concepts explained here, and should not be used in a production environment.</span></span>  
  
  
