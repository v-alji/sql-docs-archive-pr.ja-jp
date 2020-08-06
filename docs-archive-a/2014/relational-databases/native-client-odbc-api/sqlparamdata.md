---
title: SQLParamData |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLParamData function
ms.assetid: 92349482-ea22-4a6a-8484-e9c6566794fa
author: rothja
ms.author: jroth
ms.openlocfilehash: a4e0e8b31a65f28ce83e0d114231bdedd7a35a4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645025"
---
# <a name="sqlparamdata"></a><span data-ttu-id="24312-102">SQLParamData</span><span class="sxs-lookup"><span data-stu-id="24312-102">SQLParamData</span></span>
  <span data-ttu-id="24312-103">SQLParamData が、テーブル値パラメーターに関連付けられた*Valueptrptr*を返す場合、アプリケーションは*StrLen_Or_Ind*を使用して sqlparamdata を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="24312-103">When SQLParamData returns the *ValuePtrPtr* associated with a table-valued parameter, the application should call SQLPutData with *StrLen_Or_Ind*.</span></span> <span data-ttu-id="24312-104">*StrLen_Or_Ind*の値が0より大きい場合は、アプリケーションが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 次のテーブル値パラメーター行のパラメーターデータを収集する準備ができていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="24312-104">If *StrLen_Or_Ind* has a value greater than 0, it means that the application is ready for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client to gather parameter data for the next table-valued parameter row.</span></span> <span data-ttu-id="24312-105">*StrLen_Or_Ind*の値が0の場合は、テーブル値パラメーターのデータ行がこれ以上存在しないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="24312-105">If *StrLen_Or_Ind* has a value of 0, it means there are no more rows of data for the table-valued parameter.</span></span> <span data-ttu-id="24312-106">詳細については、「[テーブル値パラメーターと列値のバインドとデータ転送](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24312-106">For more information, see [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="24312-107">テーブル値パラメーターの詳細については、「[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24312-107">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24312-108">参照</span><span class="sxs-lookup"><span data-stu-id="24312-108">See Also</span></span>  
 <span data-ttu-id="24312-109">[SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function) </span><span class="sxs-lookup"><span data-stu-id="24312-109">[SQLParamData](/sql/odbc/reference/syntax/sqlparamdata-function) </span></span>  
 [<span data-ttu-id="24312-110">ODBC API 実装の詳細</span><span class="sxs-lookup"><span data-stu-id="24312-110">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
