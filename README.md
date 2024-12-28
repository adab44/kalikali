#include <iostream>
#include <ns3/core-module.h>
#include <ns3/network-module.h>
#include <ns3/internet-module.h>
#include <ns3/point-to-point-module.h>
#include <ns3/applications-module.h>

using namespace ns3;

void PacketSwitching(double fileSize, double senderSpeed, double receiverBandwidth) {
    std::cout << "Packet Switching Simulation" << std::endl;
    double transmissionTime = fileSize / std::min(senderSpeed, receiverBandwidth);
    double latency = 100.0;
    double efficiency = 0.85;
    std::cout << "Transmission Time: " << transmissionTime << " seconds\n";
    std::cout << "Latency: " << latency << " ms\n";
    std::cout << "Efficiency: " << efficiency * 100 << "%\n";
}

void CircuitSwitching(double fileSize, double senderSpeed, double receiverBandwidth) {
    std::cout << "Circuit Switching Simulation" << std::endl;
    double setupTime = 2.0;
    double transmissionTime = fileSize / std::min(senderSpeed, receiverBandwidth);
    double totalTime = setupTime + transmissionTime;
    double latency = 50.0;
    double efficiency = 0.95;
    std::cout << "Total Time: " << totalTime << " seconds\n";
    std::cout << "Latency: " << latency << " ms\n";
    std::cout << "Efficiency: " << efficiency * 100 << "%\n";
}

void VirtualCircuitSwitching(double fileSize, double senderSpeed, double receiverBandwidth) {
    std::cout << "Virtual Circuit Switching Simulation" << std::endl;
    double setupTime = 1.0;
    double transmissionTime = fileSize / std::min(senderSpeed, receiverBandwidth);
    double totalTime = setupTime + transmissionTime;
    double latency = 75.0;
    double efficiency = 0.90;
    std::cout << "Total Time: " << totalTime << " seconds\n";
    std::cout << "Latency: " << latency << " ms\n";
    std::cout << "Efficiency: " << efficiency * 100 << "%\n";
}

int main(int argc, char *argv[]) {
    CommandLine cmd;
    cmd.Parse(argc, argv);

    double videoFileSizeMb = 700.0;
    double fileSizeKb = videoFileSizeMb * 8 * 1024;

    double senderSpeed = 10.0;
    double receiverBandwidth = 15.0;

    PacketSwitching(fileSizeKb, senderSpeed, receiverBandwidth);
    CircuitSwitching(fileSizeKb, senderSpeed, receiverBandwidth);
    VirtualCircuitSwitching(fileSizeKb, senderSpeed, receiverBandwidth);

    return 0;
}

