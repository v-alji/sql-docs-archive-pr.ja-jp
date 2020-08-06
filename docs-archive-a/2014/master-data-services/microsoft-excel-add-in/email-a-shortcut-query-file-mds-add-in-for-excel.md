---
title: ショートカット クエリ ファイルの電子メールでの送信 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 5d46f20a-b04a-45c7-82af-02a2baaabbd7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c6474e6213ce67b31b0ea52eb548fab19562f438
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715485"
---
# <a name="email-a-shortcut-query-file-mds-add-in-for-excel"></a><span data-ttu-id="f6963-102">ショートカット クエリ ファイルの電子メールでの送信 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="f6963-102">Email a Shortcut Query File (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="f6963-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] で、他のユーザーが確実に自分と同じデータを操作するようにするには、ショートカット クエリ ファイルをそのユーザーに電子メールで送信します。</span><span class="sxs-lookup"><span data-stu-id="f6963-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], email a shortcut query file to someone when you want to ensure they're working with the same data that you are.</span></span> <span data-ttu-id="f6963-104">ワークシートを保存して電子メールで送信するのではなく、クエリを共有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6963-104">You should share queries rather than saving the worksheet and emailing it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f6963-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="f6963-105">Prerequisites</span></span>  
 <span data-ttu-id="f6963-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="f6963-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f6963-107">Outlook 2010 以降がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6963-107">You must have Outlook 2010 or later installed.</span></span>  
  
-   <span data-ttu-id="f6963-108">Excel のアクティブなワークシートに MDS によって管理されるデータが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6963-108">You must have MDS-managed data in an active worksheet in Excel.</span></span>  
  
### <a name="to-send-a-shortcut-query-file"></a><span data-ttu-id="f6963-109">ショートカット クエリ ファイルを送信するには</span><span class="sxs-lookup"><span data-stu-id="f6963-109">To send a shortcut query file</span></span>  
  
1.  <span data-ttu-id="f6963-110">ワークシート内のデータが共有する形式であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f6963-110">Ensure that the data in the worksheet is in the format you want to share.</span></span> <span data-ttu-id="f6963-111">データのフィルター処理と列の並べ替えの詳細については、「[読み込み前のデータのフィルター選択 &#40;Excel 用 MDS アドインの&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) 」と「 [Excel 用 MDS アドイン&#41;&#40;の列の順序](reorder-columns-mds-add-in-for-excel.md)の変更」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6963-111">For more information about filtering data and reordering columns, see [Filter Data before Loading &#40;MDS Add-in for Excel&#41;](filter-data-before-exporting-mds-add-in-for-excel.md) and [Reorder Columns &#40;MDS Add-in for Excel&#41;](reorder-columns-mds-add-in-for-excel.md).</span></span>  
  
2.  <span data-ttu-id="f6963-112">**[保存と送信]** グループの **[クエリの送信]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f6963-112">In the **Save and Send** group, click **Send Query**.</span></span> <span data-ttu-id="f6963-113">電子メール メッセージが開き、ショートカット クエリ ファイルが添付されます。</span><span class="sxs-lookup"><span data-stu-id="f6963-113">An email message opens and the shortcut query file is attached.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="f6963-114">次の手順</span><span class="sxs-lookup"><span data-stu-id="f6963-114">Next Steps</span></span>  
  
-   <span data-ttu-id="f6963-115">ショートカット クエリ ファイルを開くには、電子メールの受信者は [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] をインストールしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6963-115">To open the shortcut query file, the recipient of the email must have the MDS [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)] installed.</span></span> <span data-ttu-id="f6963-116">受信者は、ファイルをダブルクリックして開くことができます。</span><span class="sxs-lookup"><span data-stu-id="f6963-116">The recipient can double-click the file to open it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6963-117">参照</span><span class="sxs-lookup"><span data-stu-id="f6963-117">See Also</span></span>  
 [<span data-ttu-id="f6963-118">ショートカット クエリ ファイル (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="f6963-118">Shortcut Query Files &#40;MDS Add-in for Excel&#41;</span></span>](shortcut-query-files-mds-add-in-for-excel.md)  
  
  
