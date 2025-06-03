# Final_Exam
Traffic Light Simulator

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Traffic Light Simulator</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background-color: #f0f0f0;
      margin: 0;
    }

    .traffic-light-container {
      width: 140px;
      background-color: #222;
      padding: 30px 20px;
      border-radius: 20px;
      display: flex;
      flex-direction: column;
      gap: 20px;
      align-items: center;
      justify-content: center;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.5);
    }

    .light {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      transition: all 0.5s ease;
    }

    .red {
      background-color: #330000;
    }

    .yellow {
      background-color: #333300;
    }

    .green {
      background-color: #003300;
    }

    .red.active {
      background-color: red;
      box-shadow: 0 0 20px red;
    }

    .yellow.active {
      background-color: yellow;
      box-shadow: 0 0 20px yellow;
    }

    .green.active {
      background-color: #00ff00;
      box-shadow: 0 0 20px #00ff00;
    }

    .controls {
      margin-top: 20px;
      text-align: center;
    }

  </style>
</head>
<body>
  <div id="root"></div>
  <script src="https://unpkg.com/react@17/umd/react.development.js"></script>
  <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

  <script type="text/babel">
    const TrafficLightSimulator = () => {
      const [activeLight, setActiveLight] = React.useState('red');
      const [isAuto, setIsAuto] = React.useState(true);

      React.useEffect(() => {
        if (!isAuto) return;
        
        const interval = setInterval(() => {
          setActiveLight(prev => {
            if (prev === 'red') return 'yellow';
            if (prev === 'yellow') return 'green';
            return 'red';
          });
        }, 3000);

        return () => clearInterval(interval);
      }, [isAuto]);

      return (
        <div>
          <div className="traffic-light-container">
            <div className={`light red ${activeLight === 'red' ? 'active' : ''}`} />
            <div className={`light yellow ${activeLight === 'yellow' ? 'active' : ''}`} />
            <div className={`light green ${activeLight === 'green' ? 'active' : ''}`} />
          </div>
        </div>
      );
    };

    ReactDOM.render(
      <TrafficLightSimulator />,
      document.getElementById('root')
    );
  </script>

  
</body>
</html>
