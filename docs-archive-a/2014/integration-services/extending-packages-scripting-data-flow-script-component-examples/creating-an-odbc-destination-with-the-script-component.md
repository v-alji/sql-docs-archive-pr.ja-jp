---
title: スクリプト コンポーネントによる ODBC 変換先の作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Script component [Integration Services], destination components
- ODBC destination [Integration Services]
- destinations [Integration Services], components
- Script component [Integration Services], examples
ms.assetid: d198c866-78f4-4a50-ae15-333160645815
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 10adff11a7e1db24d9a244c3e83949a010b606c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642182"
---
# <a name="creating-an-odbc-destination-with-the-script-component"></a><span data-ttu-id="bd1d3-102">スクリプト コンポーネントによる ODBC 変換先の作成</span><span class="sxs-lookup"><span data-stu-id="bd1d3-102">Creating an ODBC Destination with the Script Component</span></span>
  <span data-ttu-id="bd1d3-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] では、通常、[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先および [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODBC を使用して、ODBC 変換先にデータを保存します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-103">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], you typically save data to an ODBC destination by using an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination and the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider for ODBC.</span></span> <span data-ttu-id="bd1d3-104">ただし、単一のパッケージで使用するアドホックな ODBC 変換先を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-104">However, you can also create an ad hoc ODBC destination for use in a single package.</span></span> <span data-ttu-id="bd1d3-105">このアドホックな ODBC 変換先を作成するには、次の例に示すように、スクリプト コンポーネントを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-105">To create this ad hoc ODBC destination, you use the Script component as shown in the following example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bd1d3-106">複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、このスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-106">If you want to create a component that you can more easily reuse across multiple Data Flow tasks and multiple packages, consider using the code in this Script component sample as the starting point for a custom data flow component.</span></span> <span data-ttu-id="bd1d3-107">詳細については、「 [カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-107">For more information, see [Developing a Custom Data Flow Component](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd1d3-108">例</span><span class="sxs-lookup"><span data-stu-id="bd1d3-108">Example</span></span>  
 <span data-ttu-id="bd1d3-109">この例では、既存の ODBC 接続マネージャーを使用して、データ フローのデータを [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルに保存する変換先コンポーネントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-109">The following example demonstrates how to create a destination component that uses an existing ODBC connection manager to save data from the data flow into a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>  
  
 <span data-ttu-id="bd1d3-110">この例は、「[スクリプト コンポーネントによる変換先の作成](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)」で示したカスタムの [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先を変更したものです。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-110">This example is a modified version of the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination that was demonstrated in the topic, [Creating a Destination with the Script Component](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md).</span></span> <span data-ttu-id="bd1d3-111">ただし、この例のカスタムの [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 変換先は、ODBC 接続マネージャーを使用してデータを ODBC 変換先に保存するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-111">However, in this example, the custom [!INCLUDE[vstecado](../../includes/vstecado-md.md)] destination has been modified to work with an ODBC connection manager and save data to an ODBC destination.</span></span> <span data-ttu-id="bd1d3-112">こうした変更には、次の変更も含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-112">These modifications also include the following changes:</span></span>  
  
-   <span data-ttu-id="bd1d3-113">マネージド コードから ODBC 接続マネージャーの `AcquireConnection` メソッドを呼び出すことはできません。このメソッドを呼び出すと、ネイティブ オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-113">You cannot call the `AcquireConnection` method of the ODBC connection manager from managed code, because it returns a native object.</span></span> <span data-ttu-id="bd1d3-114">そのため、この例では、接続マネージャーの接続文字列を使用して、マネージド ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] データ プロバイダーで直接データ ソースに接続しています。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-114">Therefore, this sample uses the connection string of the connection manager to connect to the data source directly by using the managed ODBC [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Data Provider.</span></span>  
  
-   <span data-ttu-id="bd1d3-115">`OdbcCommand` には、位置パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-115">The `OdbcCommand` expects positional parameters.</span></span> <span data-ttu-id="bd1d3-116">パラメーターの位置は、コマンドのテキストの疑問符 (?) で示されます</span><span class="sxs-lookup"><span data-stu-id="bd1d3-116">The positions of the parameters are indicated by the question marks (?) in the text of the command.</span></span> <span data-ttu-id="bd1d3-117">(一方、`SqlCommand` では名前付きパラメーターが必要です)。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-117">(In contrast, a `SqlCommand` expects named parameters.)</span></span>  
  
 <span data-ttu-id="bd1d3-118">この例では、**AdventureWorks** サンプル データベースの **Person.Address** テーブルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-118">This example uses the **Person.Address** table in the **AdventureWorks** sample database.</span></span> <span data-ttu-id="bd1d3-119">この例では、このテーブルの第1列と第4列、つまり**int \* AddressID**\* および**nvarchar (30) City**列をデータフローに渡します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-119">The example passes the first and fourth columns, the **int\*AddressID**\* and **nvarchar(30)City** columns, of this table through the data flow.</span></span> <span data-ttu-id="bd1d3-120">「[特定の種類のスクリプト コンポーネントの開発](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)」の変換元、変換、および変換先の例でも、同じデータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-120">This same data is used in the source, transformation, and destination samples in the topic, [Developing Specific Types of Script Components](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md).</span></span>  
  
#### <a name="to-configure-this-script-component-example"></a><span data-ttu-id="bd1d3-121">このスクリプト コンポーネントの例を構成するには</span><span class="sxs-lookup"><span data-stu-id="bd1d3-121">To configure this Script Component example</span></span>  
  
1.  <span data-ttu-id="bd1d3-122">**AdventureWorks** データベースに接続する ODBC 接続マネージャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-122">Create an ODBC connection manager that connects to the **AdventureWorks** database.</span></span>  
  
2.  <span data-ttu-id="bd1d3-123">**AdventureWorks** データベースで次の Transact-SQL コマンドを実行して、変換先テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-123">Create a destination table by running the following Transact-SQL command in the **AdventureWorks** database:</span></span>  
  
    ```  
    CREATE TABLE [Person].[Address2]([AddressID] [int] NOT NULL,  
        [City] [nvarchar](30) NOT NULL)  
    ```  
  
3.  <span data-ttu-id="bd1d3-124">新しいスクリプト コンポーネントを [データ フロー] デザイナー画面に追加し、変換先として構成します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-124">Add a new Script component to the Data Flow designer surface and configure it as a destination.</span></span>  
  
4.  <span data-ttu-id="bd1d3-125">[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで、上流変換元の出力または変換の出力を変換先コンポーネントに接続します</span><span class="sxs-lookup"><span data-stu-id="bd1d3-125">Connect the output of an upstream source or transformation to the destination component in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="bd1d3-126">(変換なしで直接変換元を変換先に接続することもできます)。このサンプルを機能させるには、上流コンポーネントの出力に、**AdventureWorks** サンプル データベースの **Person.Address** テーブルにある **AddressID** 列と **City** 列を最低限含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-126">(You can connect a source directly to a destination without any transformations.) To ensure that this sample works, the output of the upstream component must include at least the **AddressID** and **City** columns from the **Person.Address** table of the **AdventureWorks** sample database.</span></span>  
  
5.  <span data-ttu-id="bd1d3-127">**[スクリプト変換エディター]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-127">Open the **Script Transformation Editor**.</span></span> <span data-ttu-id="bd1d3-128">**[入力列]** ページで、**AddressID** 列と **City** 列を選択します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-128">On the **Input Columns** page, select the **AddressID** and **City** columns.</span></span>  
  
6.  <span data-ttu-id="bd1d3-129">**[入力および出力]** ページで、入力を **MyAddressInput** などのわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-129">On the **Inputs and Outputs** page, rename the input with a more descriptive name such as **MyAddressInput**.</span></span>  
  
7.  <span data-ttu-id="bd1d3-130">**[接続マネージャー]** ページで、ODBC 接続マネージャーを追加または作成し、**MyODBCConnectionManager** などのわかりやすい名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-130">On the **Connection Managers** page, add or create the ODBC connection manager with a descriptive name such as **MyODBCConnectionManager**.</span></span>  
  
8.  <span data-ttu-id="bd1d3-131">[**スクリプト**] ページで、[**スクリプトの編集**] をクリックし、次に示すスクリプトをクラスに入力し `ScriptMain` ます。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-131">On the **Script** page, click **Edit Script**, and then enter the script shown below in the `ScriptMain` class.</span></span>  
  
9. <span data-ttu-id="bd1d3-132">スクリプト開発環境と **[スクリプト変換エディター]** を閉じ、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-132">Close the script development environment, close the **Script Transformation Editor**, and then run the sample.</span></span>  
  
    ```vb  
    Imports System.Data.Odbc  
    ...  
    Public Class ScriptMain  
        Inherits UserComponent  
  
        Dim odbcConn As OdbcConnection  
        Dim odbcCmd As OdbcCommand  
        Dim odbcParam As OdbcParameter  
  
        Public Overrides Sub AcquireConnections(ByVal Transaction As Object)  
  
            Dim connectionString As String  
            connectionString = Me.Connections.MyODBCConnectionManager.ConnectionString  
            odbcConn = New OdbcConnection(connectionString)  
            odbcConn.Open()  
  
        End Sub  
  
        Public Overrides Sub PreExecute()  
  
            odbcCmd = New OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " & _  
                "VALUES(?, ?)", odbcConn)  
            odbcParam = New OdbcParameter("@addressid", OdbcType.Int)  
            odbcCmd.Parameters.Add(odbcParam)  
            odbcParam = New OdbcParameter("@city", OdbcType.NVarChar, 30)  
            odbcCmd.Parameters.Add(odbcParam)  
  
        End Sub  
  
        Public Overrides Sub MyAddressInput_ProcessInputRow(ByVal Row As MyAddressInputBuffer)  
  
            With odbcCmd  
                .Parameters("@addressid").Value = Row.AddressID  
                .Parameters("@city").Value = Row.City  
                .ExecuteNonQuery()  
            End With  
  
        End Sub  
  
        Public Overrides Sub ReleaseConnections()  
  
            odbcConn.Close()  
  
        End Sub  
  
    End Class  
    ```  
  
    ```csharp  
    using System.Data.Odbc;  
    ...  
    public class ScriptMain :  
        UserComponent  
    {  
        OdbcConnection odbcConn;  
        OdbcCommand odbcCmd;  
        OdbcParameter odbcParam;  
  
        public override void AcquireConnections(object Transaction)  
        {  
  
            string connectionString;  
            connectionString = this.Connections.MyODBCConnectionManager.ConnectionString;  
            odbcConn = new OdbcConnection(connectionString);  
            odbcConn.Open();  
  
        }  
  
        public override void PreExecute()  
        {  
  
            odbcCmd = new OdbcCommand("INSERT INTO Person.Address2(AddressID, City) " +  
                "VALUES(?, ?)", odbcConn);  
            odbcParam = new OdbcParameter("@addressid", OdbcType.Int);  
            odbcCmd.Parameters.Add(odbcParam);  
            odbcParam = new OdbcParameter("@city", OdbcType.NVarChar, 30);  
            odbcCmd.Parameters.Add(odbcParam);  
  
        }  
  
        public override void MyAddressInput_ProcessInputRow(MyAddressInputBuffer Row)  
        {  
  
            {  
                odbcCmd.Parameters["@addressid"].Value = Row.AddressID;  
                odbcCmd.Parameters["@city"].Value = Row.City;  
                odbcCmd.ExecuteNonQuery();  
            }  
  
        }  
  
        public override void ReleaseConnections()  
        {  
  
            odbcConn.Close();  
  
        }  
    }  
    ```  
  
<span data-ttu-id="bd1d3-133">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="bd1d3-133">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="bd1d3-134">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-134">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="bd1d3-135">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="bd1d3-135">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="bd1d3-136">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="bd1d3-136">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1d3-137">参照</span><span class="sxs-lookup"><span data-stu-id="bd1d3-137">See Also</span></span>  
 [<span data-ttu-id="bd1d3-138">スクリプト コンポーネントによる変換先の作成</span><span class="sxs-lookup"><span data-stu-id="bd1d3-138">Creating a Destination with the Script Component</span></span>](../extending-packages-scripting-data-flow-script-component-types/creating-a-destination-with-the-script-component.md)  
  
  
