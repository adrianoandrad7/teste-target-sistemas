# Teste Target Sistemas

## 1) R: 77

## 2) Descubra a lógica e complete o próximo elemento:

- a) 1, 3, 5, 7, 9
- b) 2, 4, 8, 16, 32, 64, 128
- c) 0, 1, 4, 9, 16, 25, 36, 49
- d) 4, 16, 36, 64, 100
- e) 1, 1, 2, 3, 5, 8, 13
- f) 2, 10, 12, 16, 17, 18, 19, 20

## 3) Código para análise de faturamento:

```csharp
public class AnaliseFaturamento
{
    private double menorValorFaturamento = double.MaxValue;
    private double maiorValorFaturamento = 0;
    private int diasAcimaMedia = 0;
    private double somaFaturamento = 0;
    private int numeroDiasComFaturamento = 0;
    private double[] faturamento;

    public AnaliseFaturamento(double[] faturamento)
    {
        this.faturamento = faturamento;
    }

    public void Analisar()
    {
        for (int i = 0; i < faturamento.Length; i++)
        {
            double valor = faturamento[i];

            if (valor == 0)
                continue;

            somaFaturamento += valor;
            numeroDiasComFaturamento++;

            if (valor > maiorValorFaturamento)
                maiorValorFaturamento = valor;

            if (valor < menorValorFaturamento)
                menorValorFaturamento = valor;
        }

        double mediaAnual = CalcularMediaAnual();

        for (int i = 0; i < faturamento.Length; i++)
        {
            if (faturamento[i] > mediaAnual)
                diasAcimaMedia++;
        }

        ExibirResultados(mediaAnual);
    }

    private double CalcularMediaAnual()
    {
        return somaFaturamento / numeroDiasComFaturamento;
    }

    private void ExibirResultados(double mediaAnual)
    {
        Console.WriteLine($"Média Anual: {mediaAnual}");
        Console.WriteLine($"Maior Valor: {maiorValorFaturamento}");
        Console.WriteLine($"Menor Valor: {menorValorFaturamento}");
        Console.WriteLine($"Número de dias acima da média: {diasAcimaMedia}");
    }
}
```

## 4) Modelo lógico:

![Modelo lógico](teste-target-sistemas/logo.png)

Consulta SQL:

```sql
SELECT c.id, c.razaoSocial, t.numero, e.nomeEstado
FROM Clientes AS c
INNER JOIN Telefones AS t ON c.Id = t.idClientes
INNER JOIN Estados AS e ON c.idEstado = e.Id
WHERE e.nomeEstado = 'SP';
```

## 5) Cálculo de cruzamento entre veículos:

### Velocidade dos veículos:
- O carro está se movendo a 90 km/h.
- O caminhão está se movendo a 80 km/h.

### Impacto dos pedágios:
- 3 pedágios x 5 minutos = 15 minutos de atraso para o caminhão.

### Distância percorrida até o ponto de cruzamento:
Durante os 44 minutos (0,735 horas), podemos calcular as distâncias percorridas por ambos:

- O caminhão, viajando a 80 km/h, percorreu:
  - Distância do caminhão = 80 km/h x 0,735 = **58,8 km**.
  
- O carro, viajando a 90 km/h (sem pedágios), teria percorrido:
  - Distância do carro = 90 km/h x 0,735 = **66,15 km**.

No entanto, devido ao atraso de 15 minutos (0,25 horas) pelos pedágios, a velocidade efetiva do carro é reduzida, e podemos concluir que o caminhão estará mais próximo de Ribeirão Preto quando ambos se cruzarem.
```