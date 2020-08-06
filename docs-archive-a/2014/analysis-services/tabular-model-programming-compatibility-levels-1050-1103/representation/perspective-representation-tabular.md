---
title: パースペクティブ表現 (表形式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 6d2636c4-dae4-448f-a1d4-dbee739e177c
author: minewiskan
ms.author: owend
ms.openlocfilehash: ca8a66d3134748fd524dc0c6b524d944213533e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634684"
---
# <a name="perspective-representation-tabular"></a><span data-ttu-id="432c7-102">パースペクティブ表現 (テーブル)</span><span class="sxs-lookup"><span data-stu-id="432c7-102">Perspective Representation (Tabular)</span></span>
  <span data-ttu-id="432c7-103">パースペクティブは、クライアント アプリケーション向けに、テーブル モデルをより小さな部分に簡素化したり絞りこんだりするメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="432c7-103">A perspective is a mechanism to simplify or focus the model into a smaller portion of it for the client application.</span></span>  
  
 <span data-ttu-id="432c7-104">パースペクティブ表現の作成および操作方法の詳細については、「[パースペクティブ表現 (表形式)](perspective-representation-tabular.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="432c7-104">See [Perspective Representation (Tabular)](perspective-representation-tabular.md) for a detailed explanation on how to create and manipulate the perspective representation.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="432c7-105">パースペクティブはセキュリティ メカニズムではありません。パースペクティブの外にあるオブジェクトも、ユーザーは他のインターフェイスを利用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="432c7-105">Perspectives are not a security mechanism; objects outside the perspective can still be accessed by the user through other interfaces.</span></span>  
  
## <a name="perspective-representation"></a><span data-ttu-id="432c7-106">パースペクティブ表現</span><span class="sxs-lookup"><span data-stu-id="432c7-106">Perspective Representation</span></span>  
 <span data-ttu-id="432c7-107">AMO オブジェクトの場合、パースペクティブ表現は <xref:Microsoft.AnalysisServices.Perspective> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。</span><span class="sxs-lookup"><span data-stu-id="432c7-107">In terms of AMO objects a perspective representation has a one to one mapping relationship with <xref:Microsoft.AnalysisServices.Perspective> and no other main AMO objects are required.</span></span>  
  
### <a name="perspective-in-amo"></a><span data-ttu-id="432c7-108">AMO におけるパースペクティブ</span><span class="sxs-lookup"><span data-stu-id="432c7-108">Perspective in AMO</span></span>  
 <span data-ttu-id="432c7-109">次のコード スニペットでは、テーブル モデルでパースペクティブを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="432c7-109">The following code snippet shows how to create a perspective in a Tabular model.</span></span> <span data-ttu-id="432c7-110">このコードで中心となる要素は、perspectiveElements です。このオブジェクトは、ユーザーに提示されるテーブル モデルのすべてのオブジェクトをグラフィカルに表現したものです。</span><span class="sxs-lookup"><span data-stu-id="432c7-110">The key element in this piece of code is the perspectiveElements; this object is a graphical representation of all the objects in the tabular model that are exposed to the user.</span></span> <span data-ttu-id="432c7-111">*perspectiveElements*には4つの列が含まれています。このシナリオでは、列1、2、および3のみが関連しています。</span><span class="sxs-lookup"><span data-stu-id="432c7-111">*perspectiveElements* contains 4 columns and for this scenario only columns 1, 2 and 3 are relevant.</span></span> <span data-ttu-id="432c7-112">列 1 には表示される要素の型が格納されます (elementTypeValue)。列 2 には要素の完全な名前が格納されます。ほとんどの場合、この名前はパースペクティブに要素を入力するために解析する必要があります。列 3 にはチェック ボックスの項目が格納されます (checkedElement)。これによって、要素がパースペクティブに含まれているかどうかが指定されます。</span><span class="sxs-lookup"><span data-stu-id="432c7-112">Column 1 contains the type of element displayed -elementTypeValue-; column 2 contains the complete name of the element --, that probably will need to parsed to enter the element in the perspective; column 3 contains a checkbox item -checkedElement- that tells if the element is part of the perspective or not.</span></span>  
  
```  
  
private void updatePerspective_Click(  
                     AMO.Cube modelCube  
                  ,  DataGridView perspectiveElements  
                  ,  string updatedPerspectiveID  
             )  
{  
    //Update is done by delete first, create new and insert after  
    //if perspective doesn't exist then create first and insert after  
    updatedPerspectiveID = updatedPerspectiveID.Trim();  
    if (modelCube.Perspectives.Contains(updatedPerspectiveID))  
    {  
        modelCube.Perspectives.Remove(updatedPerspectiveID, true);  
        newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
    }  
    AMO.Perspective currentPerspective = modelCube.Perspectives.Add(updatedPerspectiveID, updatedPerspectiveID);  
  
    foreach (DataGridViewRow currentDGVRow in perspectiveElements.Rows)  
    {  
        bool checkedElement = (bool)currentDGVRow.Cells[3].Value;  
        if (checkedElement)  
        {  
            string elementTypeValue = currentDGVRow.Cells[1].Value.ToString();  
            string elementNameValue = currentDGVRow.Cells[2].Value.ToString();  
            switch (elementTypeValue)  
            {  
                case "Column: Attribute":  
                case "Column: Calculated Column":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionAttributeName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Attributes.Contains(perspectiveDimensionAttributeName))  
                        {  
                            currentPerspectiveDimension.Attributes.Add(perspectiveDimensionAttributeName);  
                        }  
                    }  
                    break;  
                case "Hierarchy":  
                    {  
                        string perspectiveDimensionName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string perspectiveDimensionHierarchyName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        AMO.PerspectiveDimension currentPerspectiveDimension;  
                        if (!currentPerspective.Dimensions.Contains(perspectiveDimensionName))  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions.Add(perspectiveDimensionName);  
                        }  
                        else  
                        {  
                            currentPerspectiveDimension = currentPerspective.Dimensions[perspectiveDimensionName];  
                        }  
                        if (!currentPerspectiveDimension.Hierarchies.Contains(perspectiveDimensionHierarchyName))  
                        {  
                            currentPerspectiveDimension.Hierarchies.Add(perspectiveDimensionHierarchyName);  
                        }  
                    }  
                    break;  
                case "Measure":  
                    {  
                        string perspectiveMeasureGroupName = Regex.Match(elementNameValue, @"(?<=')(.*?)(?=')").ToString();  
                        string measureName = Regex.Match(elementNameValue, @"(?<=\[)(.*?)(?=\])").ToString();  
                        string perspectiveMeasureName = string.Format("[Measures].[{0}]", measureName);  
                        AMO.PerspectiveCalculation currentPerspectiveCalculation = new AMO.PerspectiveCalculation(perspectiveMeasureName, AMO.PerspectiveCalculationType.Member);  
                        if (!currentPerspective.Calculations.Contains(perspectiveMeasureName))  
                        {  
                            currentPerspective.Calculations.Add(currentPerspectiveCalculation);  
                        }  
                        if (modelCube.MdxScripts["MdxScript"].CalculationProperties.Contains(string.Format("KPIs.[{0}]", measureName)))  
                        {//Current Measure is also a KPI ==> will be added to the KPIs collection of the perspective  
                            AMO.PerspectiveKpi currentPerspectiveKpi = new AMO.PerspectiveKpi(perspectiveMeasureName);  
                            if (!currentPerspective.Kpis.Contains(perspectiveMeasureName))  
                            {  
                                currentPerspective.Kpis.Add(currentPerspectiveKpi);  
                            }  
                        }  
                    }  
                    break;  
                default:  
                    break;  
            }  
        }  
    }  
  
    newDatabase.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.CreateOrReplace);  
    MessageBox.Show(String.Format("Perpective successfully updated."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
}  
  
```  
  
## <a name="amo2tabular-sample"></a><span data-ttu-id="432c7-113">AMO2Tabular サンプル</span><span class="sxs-lookup"><span data-stu-id="432c7-113">AMO2Tabular sample</span></span>  
 <span data-ttu-id="432c7-114">ただし、AMO を使用してパースペクティブ表現の作成と操作を行う方法については、AMO to Tabular サンプルのソース コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="432c7-114">However, to have an understanding on how to use AMO to create and manipulate perspective representations see the source code of the AMO to Tabular sample.</span></span> <span data-ttu-id="432c7-115">このサンプルは、Codeplex から入手できます。</span><span class="sxs-lookup"><span data-stu-id="432c7-115">The sample is available at Codeplex.</span></span> <span data-ttu-id="432c7-116">このコードに関する重要な注意事項: このコードは、ここで説明する論理的概念を補足するためにのみ提供されています。運用環境では使用しないでください。教育目的以外の目的にも使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="432c7-116">An important note about the code: the code is provided only as a support to the logical concepts explained here and should not be used in a production environment; nor should it be used for other purpose other than the pedagogical one.</span></span>  
  
  
