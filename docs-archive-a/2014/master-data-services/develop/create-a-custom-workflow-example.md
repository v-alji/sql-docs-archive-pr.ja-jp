---
title: カスタム ワークフローの例 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: dfd1616c-a75c-4f32-bdb1-7569e367bf41
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ee9d6e18bf4e54ae5eb6af6a56494fff0db28684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712086"
---
# <a name="custom-workflow-example-master-data-services"></a>カスタム ワークフローの例 (Master Data Services)
  では、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] カスタムワークフロークラスライブラリを作成するときに、MasterDataServices インターフェイスを実装するクラスを作成します。このクラスは、 [iworkflowtypeextender](/previous-versions/sql/sql-server-2016/hh758785(v=sql.130))インターフェイスを実装します。 このインターフェイスには、 [MasterDataServices](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))という1つのメソッドが含まれています。このメソッドは、ワークフローの開始時に SQL Server MDS Workflow Integration Service によって呼び出されます。 [MasterDataServices](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))メソッドには、2つのパラメーターが含まれています。 *workflowtype*には、の [**ワークフローの種類**] テキストボックスに入力したテキストが含まれ、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] *dataelement*には、ワークフロービジネスルールをトリガーしたアイテムのメタデータとアイテムデータが含まれています。  
  
## <a name="custom-workflow-example"></a>カスタム ワークフローの例  
 次のコード例は、 [MasterDataServices](/previous-versions/sql/sql-server-2016/hh759009(v=sql.130))メソッドを実装して、ワークフロービジネスルールをトリガーした要素の XML データから Name、code、および LastChgUserName 属性を抽出する方法、およびストアドプロシージャを呼び出して別のデータベースに挿入する方法を示していますが、この方法を示しています。 アイテム データ XML の例と、それに含まれるタグの説明については、「[カスタム ワークフロー XML の説明 &#40;マスター データ サービス&#41;](create-a-custom-workflow-xml-description.md)」を参照してください。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.Data.SqlClient;  
using System.Xml;  
  
using Microsoft.MasterDataServices.Core.Workflow;  
  
namespace MDSWorkflowTestLib  
{  
    public class WorkflowTester : IWorkflowTypeExtender  
    {  
        #region IWorkflowTypeExtender Members  
  
        public void StartWorkflow(string workflowType, System.Xml.XmlElement dataElement)  
        {  
            // Extract the attributes we want out of the element data.  
            XmlNode NameNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Name");  
            XmlNode CodeNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/Code");  
            XmlNode EnteringUserNode = dataElement.SelectSingleNode("//ExternalAction/MemberData/LastChgUserName");  
  
            // Open a connection on the workflow database.  
            SqlConnection workflowConn = new SqlConnection(@"Data Source=<Server instance>; Initial Catalog=WorkflowTest; Integrated Security=True");  
  
            // Create a command to call the stored procedure that adds a new user to the workflow database.  
            SqlCommand addCustomerCommand = new SqlCommand("AddNewCustomer", workflowConn);  
            addCustomerCommand.CommandType = System.Data.CommandType.StoredProcedure;  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Name", NameNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@Code", CodeNode.InnerText));  
            addCustomerCommand.Parameters.Add(new SqlParameter("@EnteringUser", EnteringUserNode.InnerText));  
  
            // Execute the command.  
            workflowConn.Open();  
            addCustomerCommand.ExecuteNonQuery();  
            workflowConn.Close();  
        }  
  
        #endregion  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [カスタム ワークフローの作成 &#40;マスター データ サービス&#41;](create-a-custom-workflow-master-data-services.md)  
  
  
