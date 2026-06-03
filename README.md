# Video Factory Adapter

Assignment deliverable for the **Design Patterns** course at **Fontys ICT** (Spring 2020, Year 2). A C# console application demonstrating the **Factory Method** and **Adapter** design patterns through a video player system supporting VHS, DVD, and BluRay formats.

## Design Patterns

### Factory Method

Each media format has its own factory (`VHSFactory`, `DVDFactory`, `BluRayFactory`) implementing `IFactory`. A factory creates a compatible video–player pair and enforces format capacity limits.

### Adapter

The concrete players (`VHSPlayer`, `DVDPlayer`, `BluRayPlayer`) only accept their specific video type. Adapters (`VHSAdapter`, `DVDAdapter`, `BluRayAdapter`) implement the generic `IVideoPlayer` interface and delegate to the concrete player after a runtime type check.

## Project Structure

```
VideoApp/
├── IVideo.cs              # Video interface
├── IVideoPlayer.cs        # Player interface
├── IFactory.cs            # Factory interface
├── VHS.cs / DVD.cs / BluRay.cs               # Video types
├── VHSPlayer.cs / DVDPlayer.cs / BluRayPlayer.cs  # Concrete players
├── VHSAdapter.cs / DVDAdapter.cs / BluRayAdapter.cs # Adapters
├── VHSFactory.cs / DVDFactory.cs / BluRayFactory.cs # Factories
└── Client.cs              # Entry point

VideoTests/                 # MSTest unit tests
```

## Class Diagram

```
┌──────────┐         ┌──────────────┐       ┌──────────┐
│  IVideo  │         │ IVideoPlayer │       │ IFactory │
└────┬─────┘         └──────┬───────┘       └────┬─────┘
     │                      │                    │
 ┌───┼────┐         ┌──────┼────────┐    ┌──────┼────────┐
 VHS DVD  BluRay   VHS    DVD     BluRay VHS   DVD   BluRay
                 Adapter Adapter  Adapter Factory Factory Factory
                   │       │        │
                   ▼       ▼        ▼
                VHS     DVD     BluRay
               Player  Player  Player
```

## How to Run

```bash
dotnet run --project VideoApp
dotnet test VideoTests