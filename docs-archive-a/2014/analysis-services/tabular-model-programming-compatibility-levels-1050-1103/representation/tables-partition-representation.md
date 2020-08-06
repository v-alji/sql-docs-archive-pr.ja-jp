---
title: パーティション表現 (表形式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: b606cd63-755c-4ac0-b19b-95b5363afbdf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6a29f273a584f3e60c6cf6458751965158cf8704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738832"
---
# <a name="partition-representation-tabular"></a><span data-ttu-id="cefbd-102">パーティション表現 (テーブル)</span><span class="sxs-lookup"><span data-stu-id="cefbd-102">Partition Representation (Tabular)</span></span>
  <span data-ttu-id="cefbd-103">運用上の目的のために、結合させるとテーブルを形成する異なる行のサブセットにテーブルを分割することができます。それぞれのサブセットがテーブルのパーティションです。</span><span class="sxs-lookup"><span data-stu-id="cefbd-103">For operational purposes, a table can be divided in different subsets of rows that when combined together form the table; each of those subsets is a partition of the table.</span></span>  
  
## <a name="partition-representation"></a><span data-ttu-id="cefbd-104">パーティション表現</span><span class="sxs-lookup"><span data-stu-id="cefbd-104">Partition Representation</span></span>  
 <span data-ttu-id="cefbd-105">AMO オブジェクトの場合、パーティション表現は <xref:Microsoft.AnalysisServices.Partition> と一対一マッピングのリレーションシップにあり、その他の主要 AMO オブジェクトを必要としません。</span><span class="sxs-lookup"><span data-stu-id="cefbd-105">In terms of AMO objects a partition representation has a one to one mapping relationship with <xref:Microsoft.AnalysisServices.Partition> and no other main AMO objects are required</span></span>  
  
### <a name="partition-in-amo"></a><span data-ttu-id="cefbd-106">AMO におけるパーティション</span><span class="sxs-lookup"><span data-stu-id="cefbd-106">Partition in AMO</span></span>  
 <span data-ttu-id="cefbd-107">AMO を使用してパーティションを管理する場合、テーブル モデル テーブルを表すメジャー グループを探して、そこから作業する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cefbd-107">When using AMO to manage a partition in a you need to find the measure group that represents the Tabular Model table and work from there.</span></span>  
  
 <span data-ttu-id="cefbd-108">次のコード スニペットでは、パーティションを既存のテーブル モデル テーブルに渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cefbd-108">The following code snippet shows how to add a partition to an existing tabular model table.</span></span>  
  
```  
  
private void AddPartition(  
                     AMO.Cube modelCube  
                  ,  AMO.DataSource newDatasource  
                  ,  string mgName  
                  ,  string newPartitionName  
                  , string partitionSelectStatement  
                  , Boolean processPartition  
             )  
{  
    mgName = mgName.Trim();  
    newPartitionName = newPartitionName.Trim();  
    partitionSelectStatement = partitionSelectStatement.Trim();  
    //Validate Input  
    if (string.IsNullOrEmpty(newPartitionName) || string.IsNullOrWhiteSpace(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (modelCube.MeasureGroups[mgName].Partitions.ContainsName(newPartitionName))  
    {  
        MessageBox.Show(String.Format("Partition Name already defined. Duplicated names are not allowed"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    if (string.IsNullOrEmpty(partitionSelectStatement) || string.IsNullOrWhiteSpace(partitionSelectStatement))  
    {  
        MessageBox.Show(String.Format("Select statement cannot be empty or blank"), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    //Input validated  
    string partitionID = newPartitionName; //Using partition name as the ID  
    AMO.Partition currentPartition = new AMO.Partition(partitionID, partitionID);  
    currentPartition.StorageMode = AMO.StorageMode.InMemory;  
    currentPartition.ProcessingMode = AMO.ProcessingMode.Regular;  
    currentPartition.Source = new AMO.QueryBinding(newDatasource.ID, partitionSelectStatement);  
    modelCube.MeasureGroups[mgName].Partitions.Add(currentPartition);  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        if (processPartition)  
        {  
            modelCube.MeasureGroups[mgName].Partitions[partitionID].Process(AMO.ProcessType.ProcessFull);  
            MessageBox.Show(String.Format("Partition successfully processed."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
        }  
  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
## <a name="amo2tabular-sample"></a><span data-ttu-id="cefbd-109">AMO2Tabular サンプル</span><span class="sxs-lookup"><span data-stu-id="cefbd-109">AMO2Tabular sample</span></span>  
 <span data-ttu-id="cefbd-110">ただし、AMO を使用してパーティション表現の作成と操作を行う方法については、AMO to Tabular サンプルのソース コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cefbd-110">However, to have an understanding on how to use AMO to create and manipulate partition representations see the source code of the AMO to Tabular sample.</span></span> <span data-ttu-id="cefbd-111">このサンプルは、Codeplex から入手できます。</span><span class="sxs-lookup"><span data-stu-id="cefbd-111">The sample is available at Codeplex.</span></span> <span data-ttu-id="cefbd-112">このコードに関する重要な注意事項: このコードは、ここで説明する論理的概念を補足するためにのみ提供されています。運用環境では使用しないでください。教育目的以外の目的にも使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="cefbd-112">An important note about the code: the code is provided only as a support to the logical concepts explained here and should not be used in a production environment; nor should it be used for other purpose other than the pedagogical one.</span></span>  
  
  
