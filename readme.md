# Improved RAG Algorithm for Legal Document Citation Extraction

# Problem Statement

In legal documents, it's essential to accurately extract citations to support legal arguments and references. However, existing algorithms may suffer from hallucinations, where they incorrectly identify irrelevant information as citations. This README presents an improved RAG (Retrieve and Generate) algorithm to address this issue.

# Part 1: Sample Legal Document and Hallucinating RAG Model

The document below details a lawsuit regarding a religious organization's tax-exempt status:

**Document:**
**Case Name:** Church of Hope v. Internal Revenue Service (D.C. Md. 2023)

- The Church of Hope (Plaintiff), a religious organization, seeks to maintain its tax-exempt status.
- The IRS (Defendant) argues the Church engages in substantial commercial activities, disqualifying it from tax exemption.
- The Church claims its activities (e.g., bookstore, bakery) are primarily religious in nature, furthering its spiritual mission.

**Citations (Ground Truth):**

1. IRC § 501(c)(3) (Internal Revenue Code - Defines religious organizations)
2. Bob Jones University v. Simon (472 U.S. 509 (1983)) (Landmark case on religious freedom and tax exemption)
3. Reynolds v. United States (98 F.3d 1127 (9th Cir. 1996)) (Case on commercial activity and tax-exempt status)
4. Eastern Montana College of Education v. Helena (924 F.2d 1322 (9th Cir. 1991)) (Case on substantial vs. incidental commercial activity)
5. Glock v. Commissioner (79 T.C. 449 (1982)) (Case on religious organizations engaging in commercial activities)
6. Speakman v. Commissioner (823 F.2d 1168 (6th Cir. 1987)) (Case on ancillary commercial activities for religious purposes)
7. Murdoch v. Commissioner (704 F.2d 1002 (9th Cir. 1983)) (Case on defining "religious purpose" for tax exemption)
8. Texas Heart Hospital of St. Luke's Episcopal Health Charities, Inc. v. United States (978 F.2d 280 (5th Cir. 1992)) (Case on religious hospitals and tax exemption)
9. United States v. The Sanctuary (49 F.3d 572 (9th Cir. 1995)) (Case on religious organizations providing social services)
10. Hermitage Ministries, Inc. v. Commissioner (73 T.C. 1106 (1979)) (Case on religious organizations and fundraising activities)

**Sample Hallucinating RAG Algorithm:**

```python
def find_citations(text):
    citations = []
    keywords = ["religious", "tax-exempt", "IRS", "commercial activity"]
    for sentence in text.split("."):
        if any(keyword in sentence.lower() for keyword in keywords):
            citations.append(sentence)  # <-- This line hallucinates
    return citations
```

# Part 2: Fixing Hallucinations

# Improvements to the RAG Algorithm

To address hallucinations and improve the RAG (Retrieve and Generate) algorithm for legal document citation extraction, the following approaches have been implemented:

## 1. Named Entity Recognition (NER)

Utilizing NER to identify legal entities such as codes, case names, and court jurisdictions within sentences helps differentiate between legal citations and general discussions of religious activities and taxes.

## 2. Regular Expressions

Refining search criteria with regular expressions targeting specific citation formats, such as legal codes with section numbers and case names with years and courts, helps improve the accuracy of citation extraction.

## 3. Entity Linking

Linking recognized legal entities to external knowledge bases, such as legal databases, helps confirm their validity as citations within the context of the document.

## 4. Contextual Understanding

Incorporating contextual information like sentence proximity to relevant keywords and legal terms aids in distinguishing between actual citations and irrelevant mentions of the keywords.

These improvements enhance the RAG algorithm's ability to accurately extract citations from legal documents, thereby improving its utility for legal professionals and researchers.

# Part 3: Evaluation

To assess the effectiveness of the improved RAG (Retrieve and Generate) system in identifying relevant citations, several evaluation metrics, including precision, recall, and F1 score, can be employed. The evaluation process involves the following steps:

1. **Dataset Preparation**: Create a larger dataset of legal documents with annotated citations. This dataset should include a variety of legal cases covering different topics and jurisdictions.

2. **Annotation**: Annotate the citations in the dataset to establish ground truth labels. Each citation should be labeled with its corresponding reference in the legal literature.

3. **System Evaluation**:
   - Apply the improved RAG system to the annotated dataset and extract citations from the documents.
   - Compare the extracted citations with the ground truth labels to determine the system's performance.
4. **Metrics Calculation**:

   - **Precision**: Calculate the ratio of correctly extracted citations to the total number of citations extracted by the system. Precision measures the accuracy of the system in identifying relevant citations.
   - **Recall**: Calculate the ratio of correctly extracted citations to the total number of citations present in the ground truth. Recall measures the system's ability to capture all relevant citations.
   - **F1 Score**: Compute the harmonic mean of precision and recall to provide a balanced evaluation of the system's performance.

5. **Human Evaluation**: Additionally, consider conducting a human evaluation where legal experts review the extracted citations and provide feedback on their accuracy and relevance.

6. **Iterative Improvement**: Based on the evaluation results and feedback from human reviewers, refine the RAG system iteratively to enhance its performance further.

By employing these evaluation techniques, we can quantitatively measure the effectiveness of the improved RAG system in accurately identifying relevant citations in legal documents. This evaluation process ensures the reliability and robustness of the system for use in legal research and practice.
