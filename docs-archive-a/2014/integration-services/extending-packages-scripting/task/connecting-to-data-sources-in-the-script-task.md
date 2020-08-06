---
title: スクリプト タスクでのデータ ソースへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- connections [Integration Services], scripts
- Integration Services packages, connections
- connection managers [Integration Services], scripts
- scripts [Integration Services], connections
- SSIS packages, connections
- packages [Integration Services], connections
- Script task [Integration Services], connections
- Connections property
- SQL Server Integration Services packages, connections
- SSIS Script task, connections
ms.assetid: 9c008380-715b-455b-9da7-22572d67c388
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2c8374271c7972498361a83e4bbe87ad12265827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715589"
---
# <a name="connecting-to-data-sources-in-the-script-task"></a><span data-ttu-id="7b5bc-102">スクリプト タスクでのデータ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="7b5bc-102">Connecting to Data Sources in the Script Task</span></span>
  <span data-ttu-id="7b5bc-103">接続マネージャーは、パッケージ内に構成されたデータ ソースへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-103">Connection managers provide access to data sources that have been configured in the package.</span></span> <span data-ttu-id="7b5bc-104">詳細については、「[Integration Services (SSIS) の接続](../../connection-manager/integration-services-ssis-connections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-104">For more information, see [Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md).</span></span>  
  
 <span data-ttu-id="7b5bc-105">スクリプト タスクは、**Dts** オブジェクトの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> プロパティを介して、これらの接続マネージャーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-105">The Script task can access these connection managers through the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property of the **Dts** object.</span></span> <span data-ttu-id="7b5bc-106"><xref:Microsoft.SqlServer.Dts.Runtime.Connections> コレクション内の各接続マネージャーは、基になるデータ ソースへの接続方法に関する情報を格納しています。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-106">Each connection manager in the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection stores information about how to connect to the underlying data source.</span></span>  
  
 <span data-ttu-id="7b5bc-107">接続マネージャーの <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> メソッドを呼び出すと、その接続マネージャーがまだ接続されていない場合、データ ソースに接続され、ユーザーのスクリプト タスク コードで使用する適切な接続または接続情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-107">When you call the <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager.AcquireConnection%2A> method of a connection manager, the connection manager connects to the data source, if it is not already connected, and returns the appropriate connection or connection information for you to use in your Script task code.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7b5bc-108">`AcquireConnection` を呼び出す前に、接続マネージャーによって返される接続の種類を知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-108">You must know the type of connection returned by the connection manager before calling `AcquireConnection`.</span></span> <span data-ttu-id="7b5bc-109">スクリプト タスクでは `Option Strict` が有効なので、`Object` 型として返される接続は、使用する前に適切な種類の接続にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-109">Because the Script task has `Option Strict` enabled, you must cast the connection, which is returned as type `Object`, to the appropriate connection type before you can use it.</span></span>  
  
 <span data-ttu-id="7b5bc-110"><xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> プロパティによって返される <xref:Microsoft.SqlServer.Dts.Runtime.Connections> コレクションの <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> メソッドを使用すると、既存の接続をコードで使用する前に検索できます。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-110">You can use the <xref:Microsoft.SqlServer.Dts.Runtime.Connections.Contains%2A> method of the <xref:Microsoft.SqlServer.Dts.Runtime.Connections> collection returned by the <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> property to look for an existing connection before using the connection in your code.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7b5bc-111">スクリプト タスクのマネージド コードでは、OLE DB 接続マネージャーや Excel 接続マネージャーなど、アンマネージド オブジェクトを返す接続マネージャーの AcquireConnection メソッドを呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-111">You cannot call the AcquireConnection method of connection managers that return unmanaged objects, such as the OLE DB connection manager and the Excel connection manager, in the managed code of a Script task.</span></span> <span data-ttu-id="7b5bc-112">ただし、これらの接続マネージャーの ConnectionString プロパティを読み取って、データソースに直接接続することができます。そのためには、接続文字列と、system.string `OledbConnection` 名前空間**System.Data.OleDb**のを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-112">However, you can read the ConnectionString property of these connection managers, and connect to the data source directly in your code by using the connection string with an `OledbConnection` from the **System.Data.OleDb** namespace.</span></span>  
>   
>  <span data-ttu-id="7b5bc-113">アンマネージ オブジェクトを返す接続マネージャーの AcquireConnection メソッドを呼び出す必要がある場合は、[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 接続マネージャーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-113">If you must call the AcquireConnection method of a connection manager that returns an unmanaged object, use an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager.</span></span> <span data-ttu-id="7b5bc-114">OLE DB プロバイダーを使用するように [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 接続マネージャーを構成すると、接続には [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-114">When you configure the [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager to use an OLE DB provider, it connects by using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Data Provider for OLE DB.</span></span> <span data-ttu-id="7b5bc-115">この場合、AcquireConnection メソッドは、 `System.Data.OleDb.OleDbConnection` アンマネージオブジェクトではなくを返します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-115">In this case, the AcquireConnection method returns a `System.Data.OleDb.OleDbConnection` instead of an unmanaged object.</span></span> <span data-ttu-id="7b5bc-116">[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 接続マネージャーで Excel データ ソースを使用するように構成するには、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Jet を選択して Excel ファイルを指定し、**[接続マネージャー]** ダイアログ ボックスの **[すべて]** ページにある **[拡張プロパティ]** の値に「`Excel 8.0`」(Excel 97 以降の場合) と入力します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-116">To configure an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager for use with an Excel data source, select the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] OLE DB Provider for Jet, specify an Excel file, and enter `Excel 8.0` (for Excel 97 and later) as the value of **Extended Properties** on the **All** page of the **Connection Manager** dialog box.</span></span>  
  
## <a name="connections-example"></a><span data-ttu-id="7b5bc-117">接続の例</span><span class="sxs-lookup"><span data-stu-id="7b5bc-117">Connections Example</span></span>  
 <span data-ttu-id="7b5bc-118">次の例では、スクリプト タスク内での接続マネージャーへのアクセス方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-118">The following example demonstrates how to access connection managers from within the Script task.</span></span> <span data-ttu-id="7b5bc-119">このサンプルでは、**Test ADO.NET Connection** という名前の [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 接続マネージャーと **Test Flat File Connection** という名前のフラット ファイル接続マネージャーが作成および構成済みであることを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-119">The sample assumes that you have created and configured an [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager named **Test ADO.NET Connection** and a Flat File connection manager named **Test Flat File Connection**.</span></span> <span data-ttu-id="7b5bc-120">[!INCLUDE[vstecado](../../../includes/vstecado-md.md)] 接続マネージャーは、データ ソースに接続するときにすぐに使用できる `SqlConnection` オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-120">Note that the [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] connection manager returns a `SqlConnection` object that you can use immediately to connect to the data source.</span></span> <span data-ttu-id="7b5bc-121">これに対し、フラット ファイル接続マネージャーは、パスとファイル名が含まれる文字列のみを返します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-121">The Flat File connection manager, on the other hand, returns only a string that contains the path and file name.</span></span> <span data-ttu-id="7b5bc-122">フラット ファイルを開いて作業するには、`System.IO` 名前空間のメソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-122">You must use methods from the `System.IO` namespace to open and work with the flat file.</span></span>  
  
```vb  
Public Sub Main()  
  
    Dim myADONETConnection As SqlClient.SqlConnection  
    myADONETConnection = _  
        DirectCast(Dts.Connections("Test ADO.NET Connection").AcquireConnection(Dts.Transaction), _  
        SqlClient.SqlConnection)  
    MsgBox(myADONETConnection.ConnectionString, _  
        MsgBoxStyle.Information, "ADO.NET Connection")  
  
    Dim myFlatFileConnection As String  
    myFlatFileConnection = _  
        DirectCast(Dts.Connections("Test Flat File Connection").AcquireConnection(Dts.Transaction), _  
        String)  
    MsgBox(myFlatFileConnection, MsgBoxStyle.Information, "Flat File Connection")  
  
    Dts.TaskResult = ScriptResults.Success  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.Windows.Forms;  
  
public class ScriptMain  
{  
  
        public void Main()  
        {  
            SqlConnection myADONETConnection = new SqlConnection();  
            myADONETConnection = (SqlConnection)(Dts.Connections["Test ADO.NET Connection"].AcquireConnection(Dts.Transaction)as SqlConnection);  
            MessageBox.Show(myADONETConnection.ConnectionString, "ADO.NET Connection");  
  
            string myFlatFileConnection;  
            myFlatFileConnection = (string)(Dts.Connections["Test Flat File Connection"].AcquireConnection(Dts.Transaction) as String);  
            MessageBox.Show(myFlatFileConnection, "Flat File Connection");  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
  
}  
  
```  
  
<span data-ttu-id="7b5bc-123">![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="7b5bc-123">![Integration Services icon (small)](../../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="7b5bc-124">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-124">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="7b5bc-125">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="7b5bc-125">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="7b5bc-126">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="7b5bc-126">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b5bc-127">参照</span><span class="sxs-lookup"><span data-stu-id="7b5bc-127">See Also</span></span>  
 <span data-ttu-id="7b5bc-128">[SSIS&#41; 接続の Integration Services &#40;](../../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="7b5bc-128">[Integration Services &#40;SSIS&#41; Connections](../../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="7b5bc-129">接続マネージャーを作成する</span><span class="sxs-lookup"><span data-stu-id="7b5bc-129">Create Connection Managers</span></span>](../../create-connection-managers.md)  
  
  
