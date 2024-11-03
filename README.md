# dever
veiculo
package veiculos;

abstract class Veiculo {
    private String placa;
    private String marca;
    private String modelo;
    private int anoFabricacao;

    public Veiculo(String placa, String marca, String modelo, int anoFabricacao) {
        this.placa = placa;
        this.marca = marca;
        this.modelo = modelo;
        this.anoFabricacao = anoFabricacao;
    }

    public abstract double calcularIPVA();
    
    public abstract void exibirDetalhes();

    public String getPlaca() {
        return placa;
    }

    public String getMarca() {
        return marca;
    }

    public String getModelo() {
        return modelo;
    }

    public int getAnoFabricacao() {
        return anoFabricacao;
    }
}
//
package veiculos;

public class Caminhao extends Veiculo{

	private static double valorDedu = 5000;
	private static double ipva = 0.015;
	
	public Caminhao(String placa, String marca, String modelo, int anoFabricacao) {
		super(placa, marca, modelo, anoFabricacao);
	}

	public double calcularIPVA() {
		int idade = 2024 - getAnoFabricacao();
		double valorCalculado = 150000 - (idade * valorDedu);
		return valorCalculado * ipva;
	}

	public void exibirDetalhes() {
		 System.out.println("Caminhao: " + getMarca() + " " + getModelo() + ", Placa: " + getPlaca() + 
                 ", Ano: " + getAnoFabricacao() + ", IPVA: R$ " + calcularIPVA());
	
		
	}

}
//
package veiculos;

public class Carro extends Veiculo{

	private static double valorDedu = 2000;
	private static double ipva = 0.04;
	
	public Carro(String placa, String marca, String modelo, int anoFabricacao) {
		super(placa, marca, modelo, anoFabricacao);
	}

	public double calcularIPVA() {
		int idade = 2024 - getAnoFabricacao();
		double valorCalculado = 100000 - (idade * valorDedu);
		return valorCalculado * ipva;
	}

	public void exibirDetalhes() {
		 System.out.println("Carro: " + getMarca() + " " + getModelo() + ", Placa: " + getPlaca() + 
                 ", Ano: " + getAnoFabricacao() + ", IPVA: R$ " + calcularIPVA());
	
		
	}

}
//
package veiculos;

public class Onibus extends Veiculo{

	private static double valorDedu = 3000;
	private static double ipva = 0.02;
	
	public Onibus(String placa, String marca, String modelo, int anoFabricacao) {
		super(placa, marca, modelo, anoFabricacao);
	}
	public double calcularIPVA() {
		int idade = 2024 - getAnoFabricacao();
		double valorCalculado = 80000 - (idade * valorDedu);
		return valorCalculado * ipva;
	}

	public void exibirDetalhes() {
		 System.out.println("Onibus: " + getMarca() + " " + getModelo() + ", Placa: " + getPlaca() + 
                 ", Ano: " + getAnoFabricacao() + ", IPVA: R$ " + calcularIPVA());
	
		
	}
}
//
package veiculos;

public class Principal {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		Veiculo Carro = new Carro("abc-1234" , "chevrolet", "camaro", 2015);
		Veiculo Caminhao = new Caminhao("def-5678" , "Meteor", "Meteor", 2019);
		Veiculo Onibus = new Onibus("ghij-9123" , "Mercedes-Benz", "LO 916", 2014);

		Carro.exibirDetalhes();
        Caminhao.exibirDetalhes();
        Onibus.exibirDetalhes();
        }

}
//
hotel
package hotel;

	interface Servico {
	    double calcularServico(int numeroPessoas, int dias);
	}
//
package hotel;

interface Acomodacao {
    double calcularDiaria();
    void exibirDetalhes(int dias);
}
//
package hotel;

public class Simples implements Acomodacao, Servico {
    private static final double DIARIA = 100;

    public double calcularDiaria() {
        return DIARIA;
    }

    public void exibirDetalhes(int dias) {
        double total = calcularDiaria() * dias;
        System.out.println("Quarto Simples: Diária R$" + DIARIA + ", Total: R$" + total);
    }

    public double calcularServico(int numeroPessoas, int dias) {
        return (numeroPessoas * 20 + 30) * dias; 
    }
}
//
package hotel;

public class Duplo implements Acomodacao, Servico {
    private static final double DIARIA = 180;

    public double calcularDiaria() {
        return DIARIA;
    }
    public void exibirDetalhes(int dias) {
        double total = calcularDiaria() * dias;
        System.out.println("Quarto Duplo: Diária R$" + DIARIA + ", Total: R$" + total);
    }

    public double calcularServico(int numeroPessoas, int dias) {
        return (numeroPessoas * 20 + 30) * dias; 
    }
}
//
package hotel;

public class Suite implements Acomodacao, Servico{
    private static final double DIARIA = 350;

    public double calcularDiaria() {
        return DIARIA;
    }

    public void exibirDetalhes(int dias) {
        double total = calcularDiaria() * dias;
        System.out.println("Suíte: Diária R$" + DIARIA + ", Total: R$" + total);
    }

    public double calcularServico(int numeroPessoas, int dias) {
        return (numeroPessoas * 20 + 30) * dias; 
    }
}
//
package hotel;

public class Pricipal {
	 
	public static void main(String[] args) {
	        Acomodacao quartoSimples = new Simples();
	        Acomodacao quartoDuplo = new Duplo();
	        Acomodacao suite = new Suite();

	        int dias = 3; 

	        quartoSimples.exibirDetalhes(dias);
	        quartoDuplo.exibirDetalhes(dias);
	        suite.exibirDetalhes(dias);
	    }
	}
