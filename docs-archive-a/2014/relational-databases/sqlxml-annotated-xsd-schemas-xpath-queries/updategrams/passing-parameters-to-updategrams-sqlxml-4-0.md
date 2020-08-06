---
title: アップデートグラムへのパラメーターの引き渡し (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- nullvalue attribute
- passing parameters [SQLXML]
- parameters [SQLXML]
- updategrams [SQLXML], passing parameters
- null values [SQLXML]
ms.assetid: 2354e6e7-1860-471f-8711-4e374c5a4ed2
author: rothja
ms.author: jroth
ms.openlocfilehash: 4bc29de2dab3d0bc3587cb21b7005c0c23dcf7c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642703"
---
# <a name="passing-parameters-to-updategrams-sqlxml-40"></a><span data-ttu-id="4d6e3-102">アップデートグラムへのパラメーターの引き渡し (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="4d6e3-102">Passing Parameters to Updategrams (SQLXML 4.0)</span></span>
  <span data-ttu-id="4d6e3-103">アップデートグラムはテンプレートであり、パラメーターを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-103">Updategrams are templates; therefore, you can pass them parameters.</span></span> <span data-ttu-id="4d6e3-104">テンプレートにパラメーターを渡す方法の詳細については、「[アップデートグラムのセキュリティに関する考慮事項 &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-104">For more information about passing parameters to templates, see [Updategram Security Considerations &#40;SQLXML 4.0&#41;](../security/updategram-security-considerations-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="4d6e3-105">アップデートグラムでは、パラメーター値として NULL を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-105">Updategrams allow you to pass NULL as a parameter value.</span></span> <span data-ttu-id="4d6e3-106">NULL パラメーター値を渡すには、`nullvalue` 属性を指定し、</span><span class="sxs-lookup"><span data-stu-id="4d6e3-106">To pass the NULL parameter value, you specify the `nullvalue` attribute.</span></span> <span data-ttu-id="4d6e3-107">`nullvalue` 属性に割り当てられる値をパラメーター値として指定します。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-107">The value that is assigned to the `nullvalue` attribute is then provided as the parameter value.</span></span> <span data-ttu-id="4d6e3-108">アップデートグラムでは、この値は NULL として扱われます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-108">Updategrams treat this value as NULL.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4d6e3-109">`<sql:header>` および `<updg:header>` では、`nullvalue` を修飾子なしで指定し、`<updg:sync>` では、`nullvalue` を `updg:nullvalue` のように修飾子付きで指定します。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-109">In `<sql:header>` and `<updg:header>`, you should specify the `nullvalue` as unqualified; whereas, in `<updg:sync>`, you specify the `nullvalue` as qualified (for example, `updg:nullvalue`).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4d6e3-110">例</span><span class="sxs-lookup"><span data-stu-id="4d6e3-110">Examples</span></span>  
 <span data-ttu-id="4d6e3-111">次の例を使用して実際のサンプルを作成するには、 [SQLXML の例を実行するための要件](../../sqlxml/requirements-for-running-sqlxml-examples.md)を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-111">To create working samples using the following examples, you must meet the requirements specified in [Requirements for Running SQLXML Examples](../../sqlxml/requirements-for-running-sqlxml-examples.md).</span></span>  
  
 <span data-ttu-id="4d6e3-112">アップデートグラムの例を使用する前に、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-112">Before using the updategram examples, note the following:</span></span>  
  
-   <span data-ttu-id="4d6e3-113">例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-113">The examples use default mapping (that is, no mapping schema is specified in the updategram).</span></span> <span data-ttu-id="4d6e3-114">マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-114">For more examples of updategrams that use mapping schemas, see [Specifying an Annotated Mapping Schema in an Updategram &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md).</span></span>  
  
### <a name="a-passing-parameters-to-an-updategram"></a><span data-ttu-id="4d6e3-115">A.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-115">A.</span></span> <span data-ttu-id="4d6e3-116">アップデートグラムにパラメーターを渡す</span><span class="sxs-lookup"><span data-stu-id="4d6e3-116">Passing parameters to an updategram</span></span>  
 <span data-ttu-id="4d6e3-117">この例では、アップデートグラムで HumanResources.Shift テーブル内の従業員の姓を変更します。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-117">In this example, the updategram changes the last name of an employee in the HumanResources.Shift table.</span></span> <span data-ttu-id="4d6e3-118">アップデートグラムには、勤務時間を一意に識別する ShiftID と、Name の 2 つのパラメーターが渡されます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-118">The updategram is passed two parameters: ShiftID, which is used to uniquely identify a shift, and Name.</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header>  
  <updg:param name="ShiftID"/>  
  <updg:param name="Name" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="$ShiftID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="$Name" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="4d6e3-119">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="4d6e3-119">To test the updategram</span></span>  
  
1.  <span data-ttu-id="4d6e3-120">上のアップデートグラムをメモ帳にコピーし、UpdategramWithParameters.xml としてファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-120">Copy the updategram above into Notepad and save it to file as UpdategramWithParameters.xml.</span></span>  
  
2.  <span data-ttu-id="4d6e3-121">次の行を追加して、 [ADO を使用して sqlxml 4.0 クエリを実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)し、アップデートグラムを実行するための sqlxml 4.0 テストスクリプト (sqlxml4test.vbs) を準備し `cmd.Properties("Output Stream").Value = outStream` ます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-121">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value  
    cmd.Parameters.Append cmd.CreateParameter("@ShiftID",  2, 1,  0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@Name",   200, 1, 50, "New Name")  
    ```  
  
### <a name="b-passing-null-as-a-parameter-value-to-an-updategram"></a><span data-ttu-id="4d6e3-122">B.</span><span class="sxs-lookup"><span data-stu-id="4d6e3-122">B.</span></span> <span data-ttu-id="4d6e3-123">アップデートグラムにパラメーター値として NULL を渡す</span><span class="sxs-lookup"><span data-stu-id="4d6e3-123">Passing NULL as a parameter value to an updategram</span></span>  
 <span data-ttu-id="4d6e3-124">アップデートグラムを実行するときに、NULL に設定するパラメーターに "isnull" 値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-124">In executing an updategram, the "isnull" value is assigned to the parameter that you want to set to NULL.</span></span> <span data-ttu-id="4d6e3-125">アップデートグラムでは "isnull" パラメーター値が NULL に変換され、それに従って処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-125">Updategram converts the "isnulll" parameter value to NULL and processes it accordingly.</span></span>  
  
 <span data-ttu-id="4d6e3-126">次のアップデートグラムでは、従業員の役職を NULL に設定します。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-126">The following updategram sets an employee title to NULL:</span></span>  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:header nullvalue="isnull" >  
  <updg:param name="EmployeeID"/>  
  <updg:param name="ManagerID" />  
</updg:header>  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Employee EmployeeID="$EmployeeID" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Employee ManagerID="$ManagerID" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a><span data-ttu-id="4d6e3-127">アップデートグラムをテストするには</span><span class="sxs-lookup"><span data-stu-id="4d6e3-127">To test the updategram</span></span>  
  
1.  <span data-ttu-id="4d6e3-128">上のアップデートグラムをメモ帳にコピーし、UpdategramPassingNullvalues.xml としてファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-128">Copy the updategram above into Notepad and save it to file as UpdategramPassingNullvalues.xml.</span></span>  
  
2.  <span data-ttu-id="4d6e3-129">次の行を追加して、 [ADO を使用して sqlxml 4.0 クエリを実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)し、アップデートグラムを実行するための sqlxml 4.0 テストスクリプト (sqlxml4test.vbs) を準備し `cmd.Properties("Output Stream").Value = outStream` ます。</span><span class="sxs-lookup"><span data-stu-id="4d6e3-129">Prepare the SQLXML 4.0 test script (Sqlxml4test.vbs) in [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md) to execute the updategram by adding the following lines after the `cmd.Properties("Output Stream").Value = outStream`:</span></span>  
  
    ```  
    cmd.NamedParameters = True  
    ' CreateParameter arguments: Name, Type, Direction, Size, Value   
    cmd.Parameters.Append cmd.CreateParameter("@EmployeeID", 3, 1, 0, 1)  
    cmd.Parameters.Append cmd.CreateParameter("@ManagerID",  3, 1, 0, Null)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4d6e3-130">参照</span><span class="sxs-lookup"><span data-stu-id="4d6e3-130">See Also</span></span>  
 [<span data-ttu-id="4d6e3-131">SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="4d6e3-131">Updategram Security Considerations &#40;SQLXML 4.0&#41;</span></span>](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
