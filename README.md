% MODELO ENERGETICO DE UNA MICRO-RED
% Simulacion de generacion solar, eolica y demanda comunitaria
clc;
clear;
close all;
% Vector que representa las 24 horas del dia
horas = 1:24;
% GENERACION SOLAR
% La generacion solar es 0 durante la noche.
% Durante el dia aumenta hasta alcanzar 25 kW a las 12:00.
generacion_solar = [0 0 0 0 0 5 8 12 16 20 23 25 ...
    23 20 16 12 8 5 0 0 0 0 0 0];
% GENERACION EOLICA
% La generacion eolica presenta variaciones irregulares
% durante las 24 horas, sin superar los 15 kW.
generacion_eolica = [8 10 7 12 9 11 6 13 10 8 12 14 ...
    9 11 15 10 7 12 9 13 8 11 6 10];
% GENERACION HIBRIDA TOTAL
% Se suma la generacion solar y eolica hora por hora.
generacion_total = generacion_solar + generacion_eolica;
% DEMANDA DE LA COMUNIDAD
% Horas 1 a 5 y 22 a 24:
% consumo nocturno entre 2 kW y 4 kW.
%
% Horas 6 a 17:
% consumo diurno entre 6 kW y 10 kW.
%
% Horas 18 a 21:
% demanda maxima de hasta 15 kW.
demanda_comunidad = [3 2.5 3 3.5 4 6 7 8 8.5 9 ...
    8 7.5 8 9 10 9.5 10 15 15 15 15 ...
    4 3.5 3];
% e. VISUALIZACION GRAFICA
% Se grafican la generacion total y la demanda comunitariaen una misma ventana.
figure;
plot(horas, generacion_total, 'b-o', 'LineWidth', 1.5);
hold on;
plot(horas, demanda_comunidad, 'r-s', 'LineWidth', 1.5);
% Configuracion del grafico
title('Comportamiento energetico de la micro-red');
xlabel('Tiempo en horas');
ylabel('Potencia en Kilovatios');
grid on;
legend('Generacion Total', 'Demanda de la Comunidad', ...
    'Location', 'best');
% Limites del eje X
xlim([1 24]);
hold off;
