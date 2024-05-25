# dio--Design-Patterns-com-Java

Estrutura do Projeto:
ExplorandoPadroesDeProjeto
│
├── src
│   ├── main
│   │   └── java
│   │       └── explorandopadroes
│   │           ├── SingletonPattern
│   │           │   └── Singleton.java
│   │           ├── StrategyPattern
│   │           │   ├── Context.java
│   │           │   ├── Strategy.java
│   │           │   └── ConcreteStrategyA.java
│   │           ├── FacadePattern
│   │           │   ├── Facade.java
│   │           │   ├── SubSystemA.java
│   │           │   ├── SubSystemB.java
│   │           │   └── SubSystemC.java
└── pom.xml (para Maven)

Implementação dos Padrões de Projeto:

Singleton Pattern:
// Singleton.java
package explorandopadroes.SingletonPattern;

public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}

Strategy Pattern:
// Strategy.java
package explorandopadroes.StrategyPattern;

public interface Strategy {
    void execute();
}

// ConcreteStrategyA.java
package explorandopadroes.StrategyPattern;

public class ConcreteStrategyA implements Strategy {
    @Override
    public void execute() {
        System.out.println("Executing strategy A");
    }
}

// Context.java
package explorandopadroes.StrategyPattern;

public class Context {
    private Strategy strategy;

    public Context(Strategy strategy) {
        this.strategy = strategy;
    }

    public void executeStrategy() {
        strategy.execute();
    }
}

Facade Pattern:
// Facade.java
package explorandopadroes.FacadePattern;

public class Facade {
    private SubSystemA subsystemA;
    private SubSystemB subsystemB;
    private SubSystemC subsystemC;

    public Facade() {
        this.subsystemA = new SubSystemA();
        this.subsystemB = new SubSystemB();
        this.subsystemC = new SubSystemC();
    }

    public void operation() {
        subsystemA.operationA();
        subsystemB.operationB();
        subsystemC.operationC();
    }
}

// SubSystemA.java
package explorandopadroes.FacadePattern;

public class SubSystemA {
    public void operationA() {
        System.out.println("Subsystem A operation");
    }
}

// SubSystemB.java
package explorandopadroes.FacadePattern;

public class SubSystemB {
    public void operationB() {
        System.out.println("Subsystem B operation");
    }
}

// SubSystemC.java
package explorandopadroes.FacadePattern;

public class SubSystemC {
    public void operationC() {
        System.out.println("Subsystem C operation");
    }
}

Observações:
O padrão Singleton garante que uma classe tenha apenas uma instância e fornece um ponto de acesso global a essa instância.
O padrão Strategy define uma família de algoritmos, encapsula cada um deles e os torna intercambiáveis. Isso permite que o algoritmo varie independentemente dos clientes que o usam.
O padrão Facade fornece uma interface unificada para um conjunto de interfaces em um subsistema. Ele define uma interface de nível mais alto que facilita o uso do subsistema.
