---
title: インライン ワークロードを使用した XML 入力ファイルのサンプル (DTA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- sample applications [DTA]
ms.assetid: 7c04fe1d-6669-44a1-8b73-36d469e9b002
author: stevestein
ms.author: sstein
ms.openlocfilehash: 93b2ab4279378b4cd392d97a9b65f299d0e9c6dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634749"
---
# <a name="xml-input-file-sample-with-inline-workload-dta"></a><span data-ttu-id="cfe91-102">インライン ワークロードを使用した XML 入力ファイルのサンプル (DTA)</span><span class="sxs-lookup"><span data-stu-id="cfe91-102">XML Input File Sample with Inline Workload (DTA)</span></span>
  <span data-ttu-id="cfe91-103">この XML 入力ファイルのサンプルでは、ワークロードを **EventString** 要素を使用して指定しています。このサンプルをコピーして、お使いの XML エディターやテキスト エディターに貼り付けてください。</span><span class="sxs-lookup"><span data-stu-id="cfe91-103">Copy and paste this sample of an XML input file that specifies a workload with the **EventString** element into your favorite XML editor or text editor.</span></span> <span data-ttu-id="cfe91-104">個別のワークロード ファイルを使用する代わりに、 **EventString** 要素を使用して XML 入力ファイル内の [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ワークロードを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="cfe91-104">You can use the **EventString** element to specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] script workload in the XML input file instead of using a separate workload file.</span></span> <span data-ttu-id="cfe91-105">このサンプルを編集ツールにコピーした後に、 **Server**、 **Database**、 **Schema**、 **Table**、 **Workload**、 **EventString**、および **TuningOptions** 要素で指定する値を、特定のチューニング セッションの値に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="cfe91-105">After copying this sample into your editing tool, replace the values specified for the **Server**, **Database**, **Schema**, **Table**, **Workload**, **EventString**, and **TuningOptions** elements with those for your specific tuning session.</span></span> <span data-ttu-id="cfe91-106">これらの要素で使用できるすべての属性および子要素の詳細については、「 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfe91-106">For more information about all of the attributes and child elements that you can use with these elements, see the [XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md).</span></span> <span data-ttu-id="cfe91-107">以下のサンプルでは、使用できる属性や子要素の一部だけを使用しています。</span><span class="sxs-lookup"><span data-stu-id="cfe91-107">The following sample uses only a subset of available attribute and child element options.</span></span>  
  
## <a name="code"></a><span data-ttu-id="cfe91-108">コード</span><span class="sxs-lookup"><span data-stu-id="cfe91-108">Code</span></span>  
 [!code-xml[InputFileSamples#InlineWorkloadInputFile](../../snippets/xml/SQL14/dta_xml/inputfilesamples/xml/dta_xml_input_file_samples.xml#inlineworkloadinputfile)]  
  
## <a name="comments"></a><span data-ttu-id="cfe91-109">説明</span><span class="sxs-lookup"><span data-stu-id="cfe91-109">Comments</span></span>  
 <span data-ttu-id="cfe91-110">`USE database_name` ステートメントは、 **EventString** 要素に含まれるインライン ワークロードで指定できます。</span><span class="sxs-lookup"><span data-stu-id="cfe91-110">`USE database_name` statements can be specified in the inline workload that is contained in the **EventString** element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfe91-111">参照</span><span class="sxs-lookup"><span data-stu-id="cfe91-111">See Also</span></span>  
 <span data-ttu-id="cfe91-112">[データベース エンジン チューニング アドバイザーの起動および使用](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="cfe91-112">[Start and Use the Database Engine Tuning Advisor](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md) </span></span>  
 <span data-ttu-id="cfe91-113">[データベース エンジン チューニング アドバイザーからの出力の表示および操作](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="cfe91-113">[View and Work with the Output from the Database Engine Tuning Advisor](../../relational-databases/performance/view-and-work-with-the-output-from-the-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="cfe91-114">XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;</span><span class="sxs-lookup"><span data-stu-id="cfe91-114">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
