# Dyllon-Barrett---Next-Senior-Seminar-II
Senior Project
/// Represents the "persona" a user can pick to theme the app —
/// this is the hook for baseball/Union University style
/// customizations. Start simple with a
/// handful of base categories + a color. Attach
enum EventCategory: String, CaseIterable, Codable, Identifiable {
    case general
    case athlete
    case student
    case parent
    case job

    var id: String { rawValue }

    var displayName: String {
        switch self {
        case .general: return "General"
        case .athlete: return "Athlete"
        case .student: return "Student"
        case .parent: return "Parent"
        case .job: return "Job"
        }
    }

    var symbolName: String {
        switch self {
        case .general: return "star.fill"
        case .athlete: return "sportscourt.fill"
        case .student: return "graduationcap.fill"
        case .parent: return "figure.and.child.holdinghands"
        case .job: return "briefcase.fill"
        }
    }

    /// Default color per category. Users can override per-event
    /// via `Event.colorHex`, but this gives a sane default so the
    /// month view still looks organized before any customization.
    var defaultColor: Color {
        switch self {
        case .general: return .gray
        case .athlete: return .green
        case .student: return .blue
        case .parent: return .orange
        case .job: return .purple
        }
    }

    /// A small bank of encouragement lines tied to the category.
    /// This is the "verbal encouragement" feature from the proposal —
    /// swap this for a server-driven or user-editable list later.
    var encouragementLines: [String] {
        switch self {
        case .general:
            return ["You've got this.", "One step at a time.", "Keep the momentum going."]
        case .athlete:
            return ["Leave it all on the field.", "Champions train, they don't complain.", "Recover hard, come back stronger."]
        case .student:
            return ["Future you is thanking you right now.", "Small study sessions win the semester.", "You didn't come this far to stop."]
        case .parent:
            return ["You're doing better than you think.", "They won't remember the mess, they'll remember you showed up.", "Deep breath — you've handled harder days."]
        case .job:
            return ["Progress, not perfection.", "Close the laptop knowing you moved the needle.", "Your future self will thank you for finishing this."]
        }
    }

    static func randomEncouragement(for category: EventCategory) -> String {
        category.encouragementLines.randomElement() ?? "You've got this."
    }
}
