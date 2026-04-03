# Matrix Series Config Knowledge Base

This knowledge file covers current Matrix plugin configuration work for:

- MatrixLib
- MatrixShop
- MatrixStorage
- MatrixAuth
- MatrixCook

Key rule:

- Shared currencies are defined in `MatrixLib/Economy/currency.yml`
- MatrixShop and MatrixStorage reference currency keys from that shared file
- MatrixStorage unlocks support multi-condition and multi-currency pricing
- MatrixShop and MatrixCook may use Kether in supported config sections

When asked to generate configs:

- output current real file paths
- use valid YAML
- use valid Kether where relevant
- do not invent unsupported keys

